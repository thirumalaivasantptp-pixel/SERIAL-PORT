## THIRUMALAIVASAN J(212224060287)
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FDH 
MOV SCON, #50H 
SETB TR1 
MAIN_LOOP:
MOV SBUF, #'B' 
WAIT_TI:
JNB TI, WAIT_TI 
CLR TI 
END

#include<reg51.h>
void main(void)
{
unsigned char msg[]="VENKAT";
unsigned char i;
TMOD=0X20; 
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}

```
### (ii) Serial Port to Transfer a Message

```
ORG 00H 
START:
 MOV TMOD, #20H 
 MOV TH1, #0FAH 
 MOV SCON, #50H 
 SETB TR1 
 MOV DPTR, #4500H 
 SEND_MESSAGE: MOVX A, @DPTR 
  MOV SBUF, A 
 WAIT_TI:
 JNB TI, WAIT_TI 
 CLR TI 
 INC DPTR 
 SJMP SEND_MESSAGE 
 L1:SJMP L1

#include<reg51.h>
void main(void)
{
unsigned char msg[]="VENKAT";
unsigned char i;
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}


```

### OUTPUT:
<img width="579" height="430" alt="image" src="https://github.com/user-attachments/assets/8f36954d-d26a-4570-9eae-6bb297d311dd" />

<img width="617" height="344" alt="image" src="https://github.com/user-attachments/assets/b368c48f-cd28-4ad4-832c-953cd7afc438" />

### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
