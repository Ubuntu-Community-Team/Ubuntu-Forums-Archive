---
title: "wreless printer installation HELP please"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by squire_uk on 2009-02-09
HIya, I've been given this code to install my canon mp600r wifi printer, but I've got a bit stuck, please be patient, tis only my 2nd day on ubuntu!!


Code:

sudo /etc/apt/sources.list

add this line to the list, just copy and past it to the bootom of the list
Code:

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu)

open a terminal copy and paste this
Code:

sudo apt-get update

[COLOR="Red"]>> this is where I'm at >> [/COLOR]do the same for this command
Code:

sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj

Now , you will want to edit the following file
Code:

sudo gedit /usr/share/ppd/pstocanonbj/canonmp500.ppd

Look for the section which starts with *OpenUI *Resolution/Output Resolution: PickOne

And change the text to read (copy and past is the easiest method):
Code:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: “<</HWResolution[600 600]>>setpagedevice”
*Resolution 1200/1200 dpi: “<</HWResolution[1200 1200]>>setpagedevice”
*Resolution 2400/2400 dpi: “<</HWResolution[2400 2400]>>setpagedevice”
*Resolution 4800/4800 dpi: “<</HWResolution[4800 4800]>>setpagedevice”
*CloseUI: *Resolution

then add this at the end (again copy and paste)
Code:

After the section above add a completely new section as follows:

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: “2&#8243;
*CNQuality 3/Normal: “3&#8243;
*CNQuality 4/Standard: “4&#8243;
*CNQuality 5/Economy: “5&#8243;
*CloseUI: *CNQuality

now reboot Ubuntu

Turn your printer on.

Go to System->Administration->Printers

Double click new printer. Your printer should appear in the detected list of printers. Click Next. Choose the MP500 Ver.2.60 model and click next. Add some text in the description and place if you like and click Apply.


rite, so you know where I am, ([COLOR="Red"]this is where I'm at[/COLOR])

and this is what I got....

squire@ubuntu:~$ sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
[sudo] password for squire:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libcnbj-2.6

any idea's?

---

### Post by plucky on 2009-02-09
> HIya, I've been given this code to install my canon mp600r wifi printer, but I've got a bit stuck



What directions are you following?

Just tried that repository in my sources.list and all i get was ```
E: Malformed line 51 in source list /etc/apt/sources.list (dist)
``` so it doesn't like ```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu
```.

And if you click on the link,you get 404 error code "not authorized to enter".The actual website is there,but is in Japanese.

Thus the "install" will not work if the repository is not available.

---

### Post by plucky on 2009-02-09
Just found your other post on the same subject [http://ubuntuforums.org/showthread.php?t=1065099](http://ubuntuforums.org/showthread.php?t=1065099) and tried out the link which actually works.

So open a terminal and ```
gksudo gedit /etc/apt/sources.list
```

and copy and paste this line into it ```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
``` then from the terminal run the "sudo apt-get update" and the rest of the commands and see if that works.

Please do not start multiple threads on the same topic as it is frowned upon.

---

### Post by squire_uk on 2009-02-09
hiya, yea, I'd forgotten about that bit, the part of the line it didn;t like was it had a "#" missing from the start of the line, I noticed all the other lines started with #, so tried it with that, and it worked.....

i only started another post as no one was helping and lowsky said it was down to my subject heading being unhelpful, as you can't edit headings, a new thread seemed to be th onely way to get some more interest, cheers for looking into the problem for me.

---

### Post by plucky on 2009-02-09
The # just comments out that line,so if the line has the # ,then that repository is not available.

Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by squire_uk on 2009-02-09
still getting this mesage - 

E: Couldn't find package libcnbj-2.6

---

### Post by squire_uk on 2009-02-09
squire@ubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
#deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu)
#deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

---

### Post by squire_uk on 2009-02-09
I gotta get to bed, early start tomro, thanks for looking at this for me, I'll check back soon as poss after work tomoro.

cheers.

---

### Post by plucky on 2009-02-09
> **squire_uk said:**
> still getting this mesage - 

E: Couldn't find package libcnbj-2.6

That is probably because the repository hasn't been installed.Please post the output of ```
cat /etc/apt/sources.list
``` and place [noparse]```

```[/noparse] brackets around the text as it makes it easier to read.

Just saw the output of your sources.list.You need to edit the file and remove the # from the last line and then run "sudo apt-get update" 

Then try to install those files.


Good Luck

---

### Post by squire_uk on 2009-02-10
hiya again, I've managed to update all the settings listed above, updated everything, and it all seems to be fine.....

but.... (isn't there always a but)

this is the guide i'd originally found to do the install from:

[http://web.archive.org/web/20070819055405/waterseven.universebox.com/?p=29](http://web.archive.org/web/20070819055405/waterseven.universebox.com/?p=29)

the bit towards the bottom "> ADDING THE PRINTER (if connected to an ASUS router)

Turn your printer on.

Go to System->Administration->Printers

Double click new printer.Choose Network Printer of type &#8220;Unix Printer (LPD)&#8221;. Click next.

Fill in the Server Field with:

192.168.1.1(change 192.168.1.1 accordingly if your ASUS router has a different address in your network)

And in the Queue Field the text:

LPRServer

Click next.

Now, choose Maker &#8220;Canon&#8221; and Model &#8220;MP 500 v.2.60&#8243;. Click Next. Fill in the description and place fields if you like.

Click Apply.

You are done!:)"

so, issue I'm having is, the administrator printers bit, doesn;t tie in with 8.10......(it's printing not printers, the options to choose from are different...

 can anyone help with the relevent details to do the same in 8.10?

thanks.

---

### Post by plucky on 2009-02-11
> so, issue I'm having is, the administrator printers bit, doesn;t tie in with 8.10......(it's printing not printers, the options to choose from are different...

can anyone help with the relevent details to do the same in 8.10?

You need the IP address of the printer.Either the printer will tell you what it is or you can look on the router.

Click on **Server > New > Printer** and it will search for a printer.If it doesn't find it a new window will open.(See screenshot)
I think that is the window you need.Select LPD/LPR Host and printer and then fill in the IP address.

Good Luck

p.s. Can't help you further as my printer is USB and not Network,so not sure how to connect network printer.

---

