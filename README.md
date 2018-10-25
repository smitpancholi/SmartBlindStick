# SmartBlindStick
Smart stick for blind peoples
const int trigPin = 3; const int echoPin = 2; long duration, cm;

void setup() {
  // initialize serial communication with HC-06:
  Serial.begin(9600);  pinMode(trigPin, OUTPUT);  pinMode(echoPin, INPUT);
}

void loop()
{
  // The sensor is triggered by a HIGH pulse of 10 or more microseconds. // Give a short LOW pulse beforehand to ensure a clean HIGH pulse:  
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2);  
  digitalWrite(trigPin, HIGH);  
  delayMicroseconds(10);  
  digitalWrite(trigPin, LOW);
  // Read the signal from the sensor: a HIGH pulse whose  // duration is the time (in microseconds) from the sending  // of the ping to the reception of its echo off of an object.
  duration = pulseIn(echoPin, HIGH);
  // convert the time into a distance
  cm = (duration/2)/29.1;
  Serial.print(cm);delay(100);
  /*if(cm < 20)
  {
    Serial.print("d"); delay(1000);
  }
  else
  {
    Serial.print("n"); delay(1000);
  } */ 
}
