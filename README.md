# weatherforecastupates
import requests

def get_weather(city):
    api_key = "https://wttr.in/{}?format=j1".format(city)
    try:
        response = requests.get(api_key)
        if response.status_code == 200:
            data = response.json()
            current = data['current_condition'][0]
            print(f"\n🌤 Weather Report for {city.title()}")
            print("-" * 35)
            print(f"Temperature : {current['temp_C']}°C")
            print(f"Feels Like  : {current['FeelsLikeC']}°C")
            print(f"Humidity    : {current['humidity']}%")
            print(f"Weather     : {current['weatherDesc'][0]['value']}")
            print(f"Wind Speed  : {current['windspeedKmph']} km/h")
            print("-" * 35)
        else:
            print("❌ Error fetching data. Please check the city name.")
    except Exception as e:
        print("⚠️ Something went wrong:", e)

if __name__ == "__main__":
    print("=== 🌦 SIMPLE WEATHER FORECAST APP ===")
    city = input("Enter city name: ").strip()
    get_weather(city)
