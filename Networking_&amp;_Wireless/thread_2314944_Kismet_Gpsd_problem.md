---
title: "Kismet Gpsd problem"
date: 2016-02-24
forum: Networking &amp; Wireless
---

### Post by Ron_H on 2016-02-24
Hello everybody!
Im new to this and need your help!

Basically im trying to create a map of my city with all wifi networks for statistics purpose related to a project and using kismet, gpsd and a python script to tether gps from my iphone 6.

I updated everything by doing apt-get update and apt get upgrade then downloaded gpsd and gpsd-clients by apt-get install. Kismet was already installed. On my iphone i enabled usb tethering and connected my pc to it via usb. My internal ip on pc is this 172.20.10.4

Then i downloaded the iPhone-gpsd.py here [http://www.spench.net/drupal/software/iphone-gps](http://www.spench.net/drupal/software/iphone-gps) and in terminal i run 
chmod 777 iPhone-gpsd.py 
and executed 
python iPhone-gpsd.py

The output was this

python iPhone-gpsd.py
Current directory: /root
gpsd:ERROR: can't bind to IPv4 port 2947, Address already in use
gpsd:ERROR: maybe gpsd is already running!
gpsd:ERROR: can't bind to IPv4 port 2947, Address already in use
gpsd:ERROR: maybe gpsd is already running!
GPSd running
Added /dev /pts/3
HTTP Server running...

After i go on 172.20.10.4 inside safari on iphone, appears the page and i tap enable so gps start to update position on the page and inside terminal on my pc i see

172.20.10.1 - - [25/Feb/2016 04:06:29] "POST / HTTP/1.1" 200 -
Recieved 1 updates:
12.3456789,34.5678,567,789012345678
$GPRMC,12345.12,A,1234.5678,N,1234.5678,E,,,123456,,,N*12

I changed the numbers with others but the order is correct and the message also correct.
It keeps update with new coordinates when move and seems recieving everything accordingly.

The problem is after i change in kismet.conf options like this

gps=true
gpstype=gpsd
gpshost=localhost:2947

Run kismet and type YES
So server is started and it says 

INFO: Connected to a JSON-enabled GPSD version 3.11, turning on JSON mode
ERROR: No update from GPSD in 15 seconds or more, attempting to reconnect

And in main page says No GPS data (GPS not connected) Pwr: AC
18

It looks like it can't connect to gpsd or somehow gpsd is not sending data. 
Maybe i can consider iptables or configure something.

Hope you can help me somehow and i searched the web but didn't find a solution also when i use bluenmea in kismet dont see the position. I run bluenmea on android and then connect the usb to pc so type adb forward tcp:4352 tcp:4352 and then gpsd -N -n -D 5 tcp://localhost:4352 and see updates but when change in kismet gpshost=localhost:2947 cant see gps coordinates.

When i type other 
gpshost=localhost:4352
I see the satellites but no position

Thank you if someone can help me with this.
And ask if need some info.

---

### Post by Ron_H on 2016-02-27
I fixed the problem.
Basically what i did was chmod 777 iPhone-gpsd.py and edit the script adding in section 

port=gps.GPSD_PORT, options="-G -n -D 5"

the options to see details.

Then i run ./iPhone-gpsd.py

it says created this device actually /dev/pts/4

and basically what i did is leave it reaciving and open new terminal where only i type

gpsd -n -N -G -D 5 -S 1928 /dev/pts/4

and in kismet.conf i change options to gpshost=127.0.0.1:1928 using the port created

and when i open kismet it recieves coordinates.
Cheers people

---

