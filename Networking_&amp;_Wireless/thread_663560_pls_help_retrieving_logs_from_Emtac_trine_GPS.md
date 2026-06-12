---
title: "pls help retrieving logs from Emtac trine GPS"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by tobycatlin on 2008-01-10
Hi all,

I just got myself a Emtac Trine GPS device. It's a bluetooth GPS unit that also logs data to internal memory. I want to use it to geotag my photos.

I can connect to it and mount it to /dev/rfcomm4. When i cat /dev/rfcomm4 i see the stream of gps data flowing down. My question is this how do i get at the logs?

I have a pdf listing an instruction set for the device: [http://www.transplantgps.com/downloads/BTGPS_II_Trine_Data_Logger_Instruction_Set_20040521.pdf](http://www.transplantgps.com/downloads/BTGPS_II_Trine_Data_Logger_Instruction_Set_20040521.pdf)
I assume that i have to send these various instructions over the serial link and parse the response.

I also wrote a short python script that would connect and read lines off the unit and i tried writing commands back over the serial link but it didn't work. I am really stabbing in the dark and would really appreciate some help. Even if it is a shove in the right direction. 

I don't mind what language is used (would like to use python or java for personal interest). 
My final aim is to have my computer automatically pull off the logs whenever the gps unit is in range and switched on. Then parse these logs into a database. finally run over my photo library to tag up any new photos that match. Should be easy eh?

Thanks for any help

toby

---

### Post by kidders on 2008-01-11
Hi there,

The interface specification seems reasonably nice. :-) ... the style of it is very like the way modems work. Unfortunately, I can't help you with a Python script, but I *could* help you write a quick Java app if you like.

If I were you, I would extend java.io.InputStream & create some sort of "readResponse" method to replace the usual "read" methods. That way, you could write something along the lines of ...```
GPSInputStream is=new GPSInputStream("/dev/rfcomm4");
OutputStream os=new BufferedOutputStream("/dev/rfcommX");
os.write("$PSRF152,....\r\n".getBytes());
while (response=is.readResponse()) {
     System.out.println(response);     // ... or whatever goes here.
}
```

---

### Post by tobycatlin on 2008-01-11
thanks kidders

that gives me a good starting point. I'll get cracking on that over the weekend and probably bug you with some more questions.

t

---

### Post by tobycatlin on 2008-01-11
if i run the command: 
cat /dev/rfcomm4

I see the output of the gps. As i understand I can also send commands to the gps unit by running something like:
echo "$PSRF151*CKSUM<cr><lf>" > /dev/rfcomm4

This runs for a few seconds but doesn't display any response. Should CKSUM be an actual value? If so do you know what it should be? 
I read through the reference pdf again but couldn't see anything helpful.

thanks 

toby

---

### Post by tobycatlin on 2008-01-11
ah i have just found the following line:

The check sum value is the byte XOR value calculated between the '$' and '*' characters.

I'll hit google to work out how to XOR something

---

### Post by tobycatlin on 2008-01-11
This provided a neat xor nema check sum converter in python: [http://blog.lucanatali.it/2006/12/nmea-checksum-in-python.html](http://blog.lucanatali.it/2006/12/nmea-checksum-in-python.html)

but...
echo '$PSRF151*0x22<cr><lf>' > /dev/rfcomm4

didn't work either. Anyone got any ideas what i am doing wrong?

---

### Post by kidders on 2008-01-12
> **tobycatlin said:**
> Should CKSUM be an actual value? If so do you know what it should be? I read through the reference pdf again but couldn't see anything helpful.Me neither ... I was hoping you'd know what that was for hehe.

> **tobycatlin said:**
> This provided a neat xor nema check sum converter in python: [http://blog.lucanatali.it/2006/12/nmea-checksum-in-python.html](http://blog.lucanatali.it/2006/12/nmea-checksum-in-python.html)

but...
echo '$PSRF151*0x22<cr><lf>' > /dev/rfcomm4

didn't work either. Anyone got any ideas what i am doing wrong?I have no idea, I'm afraid ... does it make any difference if you write the checksum in decimal?

**Edit:** Incidentally, by ...```
echo '$PSRF151*0x22<cr><lf>'
``` ... I assume you mean ... ```
 echo -e "\$PSRF151*0x22\r\n"
```... in terms of what you actually type into your terminal, right?

---

### Post by tobycatlin on 2008-01-12
I am not sure if i am connecting to the Trine gps properly.

toby@media-box:~$ hcitool scan
Scanning ...
        00:02:C7:2B:86:D4       mGPS2B86D4

toby@media-box:~$ hcitool cc 00:02:C7:2B:86:D4
seems to work ok but then i run

toby@media-box:~$ hcitool auth 00:02:C7:2B:86:D4
Not connected.

toby@media-box:~$ hcitool con 00:02:C7:2B:86:D4
Connections:


yet it still seems to get data from the device.

toby@media-box:~$ cat /dev/rfcomm4
$GPGGA,162924.478,5132.1467,N,00003.7454,W,0,00,50.0,65.4,M,47.0,M,0.0,0000*61

$GPGSA,A,1,,,,,,,,,,,,,50.0,50.0,50.0*05

$GPGSV,2,1,08,20,71,242,00,11,67,143,00,17,43,294,00,01,37,056,00*7D

$GPGSV,2,2,08,23,27,178,00,14,13,035,00,31,12,084,00,28,08,253,00*71

$GPRMC,162924.478,V,5142.7823,N,00012.5352,W,0.000000,0.00,120108,,*03

$GPVTG,,T,,M,0.000000,N,0.000000,K*4E


is it possible i can see the gps data without being authorised but cannot send commands to it without being auth'd. I put the passcode in the hci.conf file so i don't see any reason why it wouldn't auth. Any other diagnostics i could run to see what state the device is in?

ps. i was just running the echo without the -e flag. so i tried your suggestion  echo -e "\$PSRF151*0x22\r\n" but still not response.

thanks
t

---

