---
title: "Adobe Flash Plugin Update ???"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-12-08
Hi All

Whenever I get notification of Updates I now have Adobe Flash Plugin 10 shown in Update manager, but it has no tick in the box and I am unable to tick it for update.

Any thoughts would be appreciated.

Clive

---

### Post by MelDJ on 2009-12-08
this is just my guess!:
i think it detected a newer version of flash but wants you to get it from the adobe site

---

### Post by ukripper on 2009-12-08
How did you install adobe flasplayer in first place? Through synaptic or Adobe's website? Which version of ubuntu you are running?

---

### Post by clive littlewood on 2009-12-08
Hi Mldj and Ukipper

I have just downloaded the latest .deb from Adobe and when I install it tells me I already have this version, which I thought was the case.

Ukipper I'm running Karmic.

I have just checked Update manager and the update is still there unticked but now greyed out ????

Clive

---

### Post by ukripper on 2009-12-08
> **clive littlewood said:**
> Hi Mldj and Ukipper

I have just downloaded the latest .deb from Adobe and when I install it tells me I already have this version, which I thought was the case.

Ukipper I'm running Karmic.

I have just checked Update manager and the update is still there unticked but now greyed out ????

Clive

you will need to get rid of your downlaoded installed version using deb package. As it is in repos now it wont update the package you installed by yourself -The prefered way is to remove currently installed flashplayer and install it from repos through synaptic or via apt.

Following will remove your adobe flashplayer completely:
```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
```

```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
``` 

Now install flashplayer via commandline or synpatic:
```
sudo apt-get install flashplugin-installer
```

---

### Post by clive littlewood on 2009-12-08
Thanks UKripper

Will try that and get back in a few minutes.

Clive

---

### Post by clive littlewood on 2009-12-08
Thanks again UKripper

That did the trick   :D  Once I realised you had missed the "H" off flash !!!!!!

Thanks Again

Clive

---

### Post by ukripper on 2009-12-08
> **clive littlewood said:**
> Thanks again UKripper

That did the trick   :D  Once I realised you had missed the "H" off flash !!!!!!


Sorry about that. Typed clumsily for install command. But for** rm **command, i am always bit careful and check atleast 5 times before even offer to anyone lol.

I am glad it has worked out for you though!

---

### Post by Myron Plichota on 2009-12-08
Here's how I got Flash10 installed from Adobe's website using Ubuntu8.04. This worked for me but may be bad advice for newer releases.

1) At <http://get.adobe.com/flashplayer/> select the Ubuntu8.04+ .deb download (automatically to the desktop).

2) Quit Firefox and doubleclick on the .deb icon. Follow the instructions. However, Firefox did not find the new plugin, so...

3) Open a terminal window and execute the quoted commands (without the quotes).

4) "find /usr -name libflashplayer.so"

5) "cd /usr/lib/flashplugin-nonfree"

6) "sudo mv libflashplayer.so libflashplayer.so.old" (I'm cautious).

7) "sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so ." (. = current directory)

8) Quit the terminal and run Firefox. You can confirm the v10 plugin by pointing Firefox to "about:plugins".
:popcorn:

---

