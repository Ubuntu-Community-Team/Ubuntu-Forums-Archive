---
title: "Looking for just one GPSr app that I can make work"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by fredfelter on 2008-12-20
I am a novice Ubuntu user with a lot of interest in geocaching and working with apps related to the global positioning satellite receiver (gpsr). I do not know how to build a command line on my own that will massage a program into action.

After a multi-hour search it seemed that the following programs would be the most feasible for my needs; Viking, GPSMan, gpsd and GPSDrive. Despite installing each one and following any understandable (for me) instructions I CANNOT make any one of them recognize either my serial eTrex Venture or my usb eTrex Vista C gpsr.

I would be entirely satisfied at this point to just get one of those apps to  ¨see¨ my gpsr but it will take a step by step ¨recipe¨ for me to be able to accomplish that since nothing I´ve yet found on the net has worked for me.

Thanks in advance

Ubuntu 8.04 on a Thinkpad T22.

---

### Post by eagle416 on 2008-12-20
I have the same problem. do a search for "EasyGPS on Wine".

---

### Post by Shawn Dineley on 2008-12-21
sorry double posted

---

### Post by Shawn Dineley on 2008-12-21
Hello 

   Have some exp in install gpsdrive with a usb receiver on a thinkpad. First question would be. Want version of gpsdrive did you try? The reason I ask is I've never been able to get 2.10 to work but had no problems with 2.09.But that was back in Feisty.

---

### Post by fredfelter on 2008-12-21
Thanks Eagle416 but I want to do this in pure Ubuntu. I know how to deal with Windows and use it often but that´s not my goal here.

Thanks Shawn Dineley. You are correct, it is version 2.10 of GPSDrive that I got from the Synaptic PM. I wonder why an older version would work better, that doesn´t make sense?

The problem with Linux is that one needs to be well versed in the OS language in order to use it since there are so few GUI interfaces that exist/work.

---

### Post by Shawn Dineley on 2008-12-21
Ok just install 2.10pre4 from synaptic. And got it working. I opened a terminal and typed gpsd /dev/ttyUSB0 Which started gpsd with my Usb receiver. Then typed gpsdrive and it worked.

---

### Post by fredfelter on 2008-12-21
> **Shawn Dineley said:**
> Ok just install 2.10pre4 from synaptic. And got it working. I opened a terminal and typed gpsd /dev/ttyUSB0 Which started gpsd with my Usb receiver. Then typed gpsdrive and it worked.

I had previously installed that version and it opens up saying there is no connected gpsr.
So I type ¨gpsd/dev/ttyS0¨ with my serial sTrex attached and running and it says ¨no such file or directory¨
When I type ¨gpsd¨ I get ¨can´t run with neither control socket nor devices¨.

None of that means anything to me.

---

### Post by Shawn Dineley on 2008-12-21
try leaving a space between gpsd and the device. Like gpsd /dev/ttyS0 . Also run gpsd before starting gpsdrive.

---

### Post by fredfelter on 2008-12-22
> **Shawn Dineley said:**
> try leaving a space between gpsd and the device. Like gpsd /dev/ttyS0 . Also run gpsd before starting gpsdrive.

After I type the ¨gpsd /dev/ttyS0¨ the cursor flips down a line as if it is accepting the command. But then here is what I get after typing ¨gpsdrive¨:

fred@fred-laptop:~$ gpsd /dev/ttyS0
fred@fred-laptop:~$ gpsdrive
Access denied for user 'gast'@'localhost' (using password: YES)
Creating main window
/home/fred/.gpsdrive/way.txt: No such file or directory
Using Mapnik config-file: /usr/share/gpsdrive/mapnik/osm.xml
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
cannot read shape file
connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

connection to host=/var/run/postgresql dbname=gis user=fred password= connect_timeout=4 failed
could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

cannot read shape file
cannot read shape file
Read 503 POI-Types from /usr/share/gpsdrive/map-icons/icons.xml
map_koord.txt reloaded
/home/fred/.gpsdrive/way.txt: No such file or directory
/home/fred/.gpsdrive/way.txt: No such file or directory

---

### Post by Shawn Dineley on 2008-12-22
Well I didn't setup any of the mapnik or postgresql stuff. I do get some error about it from the command line, but gpsdrive starts and works on my thinkpad. Mybe that stuff is from your previous atemps to set it up. 

It is really a good program was running. I used to use it for wardriving around my town. Not to gain access to anyone's network, but as a PC tech. I wanted to see how many wifi network were just left wide open.

---

### Post by fredfelter on 2008-12-23
I wish I could interpret the results of my terminal commands to figure out what I still need to do to configure it to work. I have a feeling I´m close but still ¨no cigar¨.

---

### Post by Shawn Dineley on 2008-12-23
Well my guess would be to completely remove any postgressql stuff from synaptic. Gpsdrive is running fine on mine without any database programs running. Postgresql is there for the openstreetmaps stuff. I've never got it to work before. The downloadable maps have always been good enough for me, and I've used it to drive half way across the U.S. Just make sure to have the maps you need before leaving.

---

### Post by gerkin on 2009-07-01
I'm using an eTrex yellow and a eTrex H with no problems on Intrepid, Crunchbang & Juanty

Check out my thread here: [http://ubuntuforums.org/showthread.php?t=875478](http://ubuntuforums.org/showthread.php?t=875478)

I will be posting a 0.4 version of my Garmin script (hopefully) in the next few days>

Feel free to and email me if you have any suggestions/questions

cheers..............gerkin

---

### Post by P Minix on 2009-09-01
Along these lines, can anyone recommend a good CLI text parser to strip out the NMEA codes?

---

