# the following program communicates with a lux and proximity sensor
# the sensor unit interfaces with a raspberry pi using a i2c bus
# it then takes in the light level and prints to console different text depending on the level of light
# it then also prints the given Lux level, the sampling rate is every 1 second 

# import all required
from time import sleep #delay function
import board # interfacing for Rasp Pi
import busio # interfacing
import adafruit_vcnl4040 # lib for the AdaFruit lux and proximity sensor

i2c = busio.I2C(board.SCL, board.SDA)
sensor = adafruit_vcnl4040.VCNL4040(i2c)
sampleRate = 1 # 1 second sample rate
lightLevelText = "" # <-- used to store the given text light condition

#Main loop
while True:
    
    #get the light level from the sensor
    luxLevel = sensor.lux 
    
    # if else statement to figure out how bright it is and print the required text
    if (luxLevel > 2000):
        lightLevelText = "Too Bright"
    elif (luxLevel <= 2000 and luxLevel > 1000):
        lightLevelText = "Bright"
    elif (luxLevel <= 1000 and luxLevel > 400):
        lightLevelText = "Medium"
    elif (luxLevel <= 400 and luxLevel > 100):
        lightLevelText = "Dark"
    else:
        lightLevelText = "Too Dark"
    
    #print the infomation to console
    print(lightLevelText + ": %d lux" % luxLevel)
    
    #sample rate delay
    sleep(sampleRate)
