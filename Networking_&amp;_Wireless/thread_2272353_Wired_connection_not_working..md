---
title: "Wired connection not working."
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by Vincii on 2015-04-06
Hey, 

So I'm new to Ubuntu and after working for hours to get it installed I got on and I set up my internet
and I went to Mozilla and it just loads for ever and does nothing.

---

### Post by flaymond on 2015-04-06
type

```
 ifconfig 
```

and print the output here.

Note : Do it while the wire/cable connected to your PC.

---

### Post by Vincii on 2015-04-06
```
eth0      Link encap:Ethernet  HWaddr 74:d4:35:56:eb:0a  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe56:eb0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:304 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85 (85.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53163 (53.1 KB)  TX bytes:53163 (53.1 KB)



```

---

### Post by praseodym on 2015-04-06
Please run the wireless-script from the sticky-thread and show the outputs.

---

### Post by Vincii on 2015-04-06
Do you mean this?

```
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
```

---

### Post by praseodym on 2015-04-07
Yes, it creates a file named wireless-info.txt, please post its content here

---

### Post by michi1983 on 2015-04-07
> **praseodym said:**
> Yes, it creates a file named wireless-info.txt, please post its content here

He doesn't even have a wifi connection though, at least that's what his ifconfig tells.

I would suggest that he tries to ping the router/modem to which his computer is connected and then try to ping the 8.8.8.8 DNS server of Google. 
If this all works and he still can't access the internet we can tell that it's a DNS problem he has.

greetz

edit: oh I see, the script also shows the routing table and dns entries in resolv.conf etc. My fault ;)
In case the TO can't download it because his internet doesn't work, I attached it here in this comment.
I took it from your comment in [this ]("http://ubuntuforums.org/showthread.php?t=2272214")post praseodym.

[ATTACH]261150[/ATTACH]

---

### Post by praseodym on 2015-04-07
It is only named "wireless-info", it also contains any networking configs ;), LAN, too.

---

### Post by Vincii on 2015-04-07
it doesn't create a .txt it just say something about not being able to download from dl.dropbox.com .

---

### Post by praseodym on 2015-04-07
Download it directly;

[http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)

and run

```
chmod +x wireless_script && ./wireless_script
```

---

### Post by Vincii on 2015-04-07
Do i have to put wireless_script.txt any where in particular ?

---

### Post by michi1983 on 2015-04-07
> **Vincii said:**
> Do i have to put wireless_script.txt any where in particular ?

Just copy its content here in your comment within code brackets from the editor

---

### Post by Vincii on 2015-04-07
No, I mean once i download the .txt file. I download it on windows then use a usb stick to put it on the desktop (Ubuntu desktop)but when i use what the other person said I doesn't work.. so I don't know if the .txt file has to be any where in particular for it to work.

[COLOR=#cccccc][FONT=verdana][SIZE=1]I bet I sound stupid :3[/SIZE][/FONT][/COLOR]

---

### Post by michi1983 on 2015-04-07
> **Vincii said:**
> No, I mean once i download the .txt file. I download it on windows then use a usb stick to put it on the desktop (Ubuntu desktop)but when i use what the other person said I doesn't work.. so I don't know if the .txt file has to be any where in particular for it to work.

[COLOR=#cccccc][FONT=verdana][SIZE=1]I bet I sound stupid :3[/SIZE][/FONT][/COLOR]

You don't sound stupid but you misunderstand something ;)
The .txt file gets created from the script.
The script itself doesn't have a file ending, because it is a script.
It's just wireless-script and not wireless-script.txt or something else.

From this file [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) just copy the content and create a new file on your windows dekstop called wireless-script (NO FILE EXTENSION).
Then copy it on your linux machine (with USB stick or whatever) and do the commands provided then it will work ;)

---

### Post by Vincii on 2015-04-07
Ok, i got the no txt thing now but when I put the wireless_script on the desktop and do

```
chmod +x wireless_script && ./wireless_script
```

it just says the file doesn't exist.


*[FONT=comic sans ms][COLOR=#cccccc]halp[/COLOR][/FONT]*

---

### Post by michi1983 on 2015-04-07
well, in the terminal you have to change to the Desktop directory before you type in the command because this command assumes that you are exactly in the directory in which the file is located.

and take care of the file name with underline_ or hyphen-

---

### Post by Vincii on 2015-04-07
So I would put

```
chmod +x wireless_script && /home/(username)/Desktop/wireless_script
```

???

*[COLOR=#cccccc]._.[/COLOR]*

---

### Post by michi1983 on 2015-04-08
Nope! It depends on where you are in your filestructure and where the script lies.

Let's make this step by step:

Please open a terminal and type ```
pwd
```.
It should return something like /home/$username, right?

Then change to your Desktop with ```
cd Desktop
```
This is where your wireless_script is located right?
You can verify that with typing ```
ls
``` in the terminal. It lists all files which are in the directory you are right now.
When you see your wireless_script you can type the original command for the script.
```
sudo chmod +x wireless_script && ./wireless_script
```

---

### Post by Vincii on 2015-04-08
Ok, I did that... still got pretty much the same thing.

```
[COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**bin**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**bash**[/FONT][/COLOR][COLOR=#545454][FONT=arial]^[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**M**[/FONT][/COLOR][COLOR=#545454][FONT=arial]: [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**bad interpreter**[/FONT][/COLOR][COLOR=#545454][FONT=arial]: no such file or directory[/FONT][/COLOR]
```

and I was in the Desktop directory. the wireless_script was green when i typed ls.

---

### Post by michi1983 on 2015-04-08
Okay it seems that you still are not in the right place ;)

Please open a terminal and type ```
cd /home/$username/Desktop
```
After that please type ```
ls
``` and post the output here in your next comment

---

### Post by Vincii on 2015-04-08
When I started the terminal i was in home/vincii(username) i typed cd Desktop and ls got wireless_script but it was green and when i tried to do

```
chmod +x wireless_script && ./wireless_script
```

it said it wasn't there.

I'm pretty sure i was in the right place. because when i did what you said last, it showed the same thing, green wireless_script.

---

### Post by michi1983 on 2015-04-08
Please tell me why don't you just post the output of ```
ls -asl /home/vincii/Desktop
``` like I asked you before?
Pictures tell more than thousand words ;)

---

