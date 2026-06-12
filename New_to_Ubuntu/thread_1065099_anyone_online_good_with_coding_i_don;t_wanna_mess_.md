---
title: "anyone online good with coding? i don;t wanna mess this &quot;up...."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by squire_uk on 2009-02-09
hiyam I need to get my wifi printer working with ubuntu,

I;ve found this guide on how to do it, but I'm only on my 2nd day with ubuntu, and had enough trouble adding the code to get my wireless network working in the first place,

I'f anyone experienced is around who fancies helping out, I'd much appreciate it.

this is the guide I'e found.

[http://web.archive.org/web/20070819055405/waterseven.universebox.com/?p=29](http://web.archive.org/web/20070819055405/waterseven.universebox.com/?p=29)

---

### Post by squire_uk on 2009-02-09
guess not then.. I'll have to hve a crack at it myself, ... then post a help, i've cocked sumthin up post as well haha.

---

### Post by LowSky on 2009-02-09
so you need help installing a printer, that is what your threads title should have been

```
sudo /etc/apt/sources.list
```

add this line to the list, just copy and past it to the bootom of the list
```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu
```

open a terminal copy and paste this
```
sudo apt-get update
```
do the same for this command
```
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

Now , you will want to edit the following file 
```

sudo gedit /usr/share/ppd/pstocanonbj/canonmp500.ppd
```

Look for the section which starts with *OpenUI *Resolution/Output Resolution: PickOne

And change the text to read (copy and past is the easiest method):
```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: “<</HWResolution[600 600]>>setpagedevice”
*Resolution 1200/1200 dpi: “<</HWResolution[1200 1200]>>setpagedevice”
*Resolution 2400/2400 dpi: “<</HWResolution[2400 2400]>>setpagedevice”
*Resolution 4800/4800 dpi: “<</HWResolution[4800 4800]>>setpagedevice”
*CloseUI: *Resolution
```

then add this at the end (again copy and paste)
```
After the section above add a completely new section as follows:

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: “2&#8243;
*CNQuality 3/Normal: “3&#8243;
*CNQuality 4/Standard: “4&#8243;
*CNQuality 5/Economy: “5&#8243;
*CloseUI: *CNQuality

```
now reboot Ubuntu

Turn your printer on.

Go to System->Administration->Printers

Double click new printer. Your printer should appear in the detected list of printers. Click Next. Choose the MP500 Ver.2.60 model and click next. Add some text in the description and place if you like and click Apply.

---

### Post by squire_uk on 2009-02-09
thanks much, I was hoping someone fancied taking over my comp remotely and doing it for me!! really am a noob to all this adding code stuff, but you've laid it the instructions alot clearer than on the tutorial, I'll give it a go now.

cheers for putting the time in.

---

### Post by squire_uk on 2009-02-09
hiya, got a bit stuck by here......

squire@ubuntu:~$ sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
[sudo] password for squire: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.6

---

