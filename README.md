- 👋 Hi, I’m @yashksingh1510
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
yashksingh1510/yashksingh1510 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#include<Servo.h>                                                          //including servo library
#include<LiquidCrystal.h>                                           //including LCD display library
const int rs = PB11, en = PB10, d4 = PA4, d5 = PA3, d6 = PA2, d7 = PA1;   //declaring pin names and pin numbers of lcd
LiquidCrystal lcd(rs,en,d4,d5,d6,d7);                     //setting lcd and its paramater
 
int servoPin = PA0;                      //declare and initialize pin for servo output PWM 
int potPin = PA5;                                     //potentiometer ADC input 
Servo servo;                                  // creating variable servo with datatype Servo
 
void setup()                            
 
{ 
  lcd.begin(16,2);                                                         
  lcd.setCursor(2,0);                                                        
  lcd.print("PWM Tutorial");                                               
  lcd.setCursor(3,1);                                                       
  lcd.print("Using Servo");                                           
  delay(3000);                                                            
  lcd.clear();                                                              
  servo.attach(servoPin);   //it connects pin PA0 with motor as control feedback by providing pulses
  
}
 
void loop()
{
 lcd.clear();                                                                 //clears lcd
 int angle;                                                                   //declare variable angle as int
 int reading;                                                                 //declare variable reading as int
 reading = analogRead(potPin);                          //read analog value from pin PA3
 angle = (reading/24);  //it divides ADC the value according to max angle 170deg
 servo.write(angle);                                                          //it puts angle value at servo
 lcd.setCursor(0,0);                                //setting cursor at first row and first column
 lcd.print("Angle:");                                                         //puts Angle in LCD
 lcd.print(angle);                                                            //puts value at angle
 delay(100);                                                                  //delay in time
} 
