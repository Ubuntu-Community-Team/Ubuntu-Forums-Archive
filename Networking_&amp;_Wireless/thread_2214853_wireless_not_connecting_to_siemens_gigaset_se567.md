---
title: "wireless not connecting to siemens gigaset se567"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by Micheal_David_Lege on 2014-04-03
i have ubuntu 11.10 and my laptop will not connect to any wireless signals that are siemens gigaset se567. my girlfriends house use to be dlink and it worked fine. then changed moden to siemens and now it keeps trying to connect but never does. so i know its the siemens that my laptop wont connect to. anyone know how i can fix this? i can plug in via the lan plug only. kinda frustrating

---

### Post by varunendra on 2014-04-05
Welcome to Ubuntu Forums! :)

When it is trying to connect and fails, please run this command -
```
sudo iwlist scan
```
..and post back its output here.

Alternatively, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a lot more info than just the info about the router signal.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Micheal_David_Lege on 2014-04-07
so i did your command and it still wont work.

---

### Post by Micheal_David_Lege on 2014-04-07
so i did the command is asked me to do in the wireless script and I got this. my wireless tries to connect but just keeps trying and trying. but its only when the wireless routers are [h=2]siemens gigaset se567[/h]
Help would be appreciate

micheal@MichealDavidLeger:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-04-07 16:30:05--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com... 204.236.219.205
Connecting to dl.dropbox.com|204.236.219.205|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-04-07 16:30:05--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com... 54.235.138.1, 23.21.47.41, 54.225.159.160, ...
Connecting to dl.dropboxusercontent.com|54.235.138.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4357 (4.3K) [text/plain]
Saving to: `wireless_script'


100%[======================================>] 4,357       --.-K/s   in 0.004s  


Last-modified header missing -- time-stamps turned off.
2014-04-07 16:30:06 (969 KB/s) - `wireless_script' saved [4357/4357]




Results archived in "wireless-info.tar.gz", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.


micheal@MichealDavidLeger:~$

---

### Post by varunendra on 2014-04-08
I posted what I need in the other thread where you posted the same above response. Please attach the result file as asked there.

---

