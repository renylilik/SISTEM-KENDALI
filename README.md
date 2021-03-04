int LDR = A0;
int LED = 3;
int dataSensor;
// Variabel motor
int pwm = 6;
int pwmA = 10;
int pwmB = 9;
int pinEnable = 7;

void setup()
{
  pinMode(LDR, INPUT); // Set pin A0 sebagai input
  pinMode(LED, OUTPUT); // Set pin 3 sebagai output
  pinMode(pwmA, OUTPUT);
  pinMode(pwmB, OUTPUT);
  pinMode(pinEnable, OUTPUT);
  Serial.begin(9600); // Baud Rate standar 9600
}

void loop()
{
  // Nilai terendah LDR = 2 (Paling Gelap)
  // Nilai tertinggi LDR = 404 (Paling Terang)
  dataSensor = analogRead(LDR);
  Serial.println(dataSensor);
  
  // Algoritma Sistem Kendali On/Off pada LED
  if (dataSensor < 100){
    digitalWrite(LED, HIGH); // Menyalakan lampu LED ketika gelap
    belokkiri();
  }
  else
    digitalWrite(LED, LOW); // Menyalakan lampu LED ketika terang
  	belokkanan();
}

void belokkiri(){
  digitalWrite(pinEnable, HIGH);
  digitalWrite(pwmA, HIGH);
  digitalWrite(pwmB, LOW);
}

void belokkanan(){
  digitalWrite(pinEnable, HIGH);
  digitalWrite(pwmA, LOW);
  digitalWrite(pwmB, HIGH);
}
