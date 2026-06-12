---
title: "need help with some command for ubuntu server"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by rawrico on 2010-10-20
First of all, i'm actually a noob user only use Ubuntu, not the server version, but this time cause of some damn thing i need to use it. So i ask what i need

-Auto connect to SAMBA server each time startup(smbfs)
-Run the [linux version uTorrent]("http://www.utorrent.com/downloads/linux") each time startup the ubuntu server
-Prioritize the startup, to determine the SAMBA first and uTorrent Start later each time startup

here is a picture i drawn to show why
[IMG]http://img.photobucket.com/albums/v289/rawrico/picture.png[/IMG]

PS:reason why i do this because i naked my eeepc 4G and to use as a BT Download Client, when the time i'm thinking to use WINDOWS wo handle it, but for the virus free problem, i rather use linux, ubuntu i used before are good with deluge, but some day later the deluge made me uncomfort, so i rather use utorrent, in the mean time i saw this LINUX version of uTorrent, so thats why i use this way, but the command things is noob to me, so i need help




EDITED
CASE SOLVED

---

### Post by SuaSwe on 2010-10-20
I'm not at all familiar with the Linux version of uTorrent - do you already have it running, and does it use a Ubuntu-type launcher? 

On a general level though, I think what you'd want to do to get an app to run at startup would be to write a little script to launch the applications, e.g.:

```

#!/bin/bash
sleep 10 &&
smbfs &&
sleep 10 &&
utorrent &&
exit

```

Then follow the instructions from thread #208954, e.g.:

> 
1- create a file under init.d : sudo gedit /etc/init.d/my_script
2- put your command lines/script in the file & save it [so add the text from above to this file, in other words]
3- make the file executable : sudo chmod +x /etc/init.d/my_script
4- make it run on boot : sudo update-rc.d my_script defaults


Something like that.

---

### Post by rawrico on 2010-10-20
thanks suaswe
the utorrent for linux is actuall must run as like

"./utserver"

without the quote
thats how it need to run

---

### Post by SuaSwe on 2010-10-20
Haha, yep, mine was just an example as I've never used uTorrent under Linux and have (had!) no idea what it's called. ;) To my knowledge, as long as you can run it from Terminal using 

```

user@pc:~$ utserver

```

... you can just pop that into the script and off you go.

---

### Post by rawrico on 2010-10-21
thanks men
thanks for reply
will try and see it works as i thought or not

will let you know once i tried

---

### Post by rawrico on 2010-10-21
Thanks you SuaSwe
i got it works with what i want
thank you

---

