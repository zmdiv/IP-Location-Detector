import requests
from pyfiglet import Figlet
import folium


def get_info_ip(ip='127.0.0.1'):  # getting data
    try:
        response = requests.get(url=f'http://ip-api.com/json/{ip}').json()

        data = {'[IP]': response.get('query'),  # creating dictionary from data
                '[Provider]': response.get('isp'),
                '[Company]': response.get('org'),
                '[Country]': response.get('country'),
                '[Region]': response.get('regionName'),
                '[City]': response.get('city'),
                '[ZIP]': response.get('zip'),
                '[Latitude]': response.get('lat'),
                '[Longitude]': response.get('lon'),

                }
        for k, v in data.items():  # printing structured data
            print(f'{k} : {v}')

        # creating the map of the received location. The script creates the html file
        # which should be opened in the browser in order to see the map

        area = folium.Map(location=[response.get('lat'), response.get('lon')])
        area.save(f'{response.get("query")}_{response.get("city")}.html')

    except requests.exceptions.ConnectionError:
        print('Connection failed')




def main():
    preview = Figlet(font='cybermedium')   # Printing project name for the preview
    print(preview.renderText('Location Detector'))
    ip = input('Enter IP address:  ')
    get_info_ip(ip=ip)


main()
