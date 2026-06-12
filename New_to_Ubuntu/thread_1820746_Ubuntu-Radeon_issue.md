---
title: "Ubuntu-Radeon issue"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Nikhil Kenvetil on 2011-08-08
hi all.. so i installed ubuntu 11.04(with Unity) onto a partition of around 92GB.. created a swap space of 8GB(twice my RAM).. first time boot was alright.. i customized ma desktop wit no issues.. but wen i rebooted the comuter n entered ubuntu, der is a no video scenario.. windows loads fine.. i also installed fedora n xubuntu (after erasing de previos OS) to test.. dey load, but der is a splash screen of something distorted wen dey boot.. any help is greatly appreciated..

---

### Post by sikander3786 on 2011-08-08
So you mean you've reinstalled Ubuntu 11.04 after trying Fedora and Xubuntu?

Is it a proper dual-boot setup or Ubuntu is installed inside Windows using Wubi?

What do get now when you boot your PC? Can you see the Ubuntu Plymouth image? How far does it go and in the end, you get a blank screen or a messed of desktop?

We also need to know which graphics card is there. If you can see the Grub menu, choose 'Recovery Mode' probably the 2nd on the list and then choose 'Drop to root shell'. Please post the output of these commands from there:

```
lshw -c video
cat /etc/X11/xorg.conf
/usr/lib/nux/unity_support_test -p
```

---

### Post by Nikhil Kenvetil on 2011-08-08
> **sikander3786 said:**
> So you mean you've reinstalled Ubuntu 11.04 after trying Fedora and Xubuntu?

Is it a proper dual-boot setup or Ubuntu is installed inside Windows using Wubi?

What do get now when you boot your PC? Can you see the Ubuntu Plymouth image? How far does it go and in the end, you get a blank screen or a messed of desktop?

We also need to know which graphics card is there. If you can see the Grub menu, choose 'Recovery Mode' probably the 2nd on the list and then choose 'Drop to root shell'. Please post the output of these commands from there:

```
lshw -c video
cat /etc/X11/xorg.conf
/usr/lib/nux/unity_support_test -p
```
[COLOR=black][FONT=Verdana]hey sikander3786.. it is a proper dual boot system. der is also windows 7 ultimate on it.. it is NOT installed inside windows.. wen de PC is turned on, it has de pink screen wit 2 ubuntu modes(the recovery Mode is guess, and the other regular mode), 2 memory tests modes, n one mode to log into windows.. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wen i select regular ubuntu it goes to a screen with a flashing cursor on de left hand top corner.. den to a lighter black screen with absolutely nothing on it.. de ubuntu insignia doesn&#8217;t come on at all..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I took out ubuntu n installed fedora 13 to test.. it loads fine, but a splash screen of something distorted comes up for a second BEFORE de login screen shows up.. same with xubuntu 10.04(not 11.04, if it is out i.e.)..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]De graphonc card I have is[/FONT][/COLOR][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][COLOR=black][FONT=Verdana]radeon 6740M[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I went itno de failsafeX mode, n it loads fine without Unity, but again, while shutting it down it was frozen on the wallpaper screen, wit no task bar or icons.. jus plain wallpaper.. it was der for almost 15 minutes[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Dis is all I could try..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Will try to imply dose commands u sent me.. if der is anything u cud make outta my post now, please lemme know[/FONT][/COLOR]

---

### Post by sikander3786 on 2011-08-08
Yeah need to see the outputs to find if your graphics card is actually capable of running Unity.

---

### Post by Nikhil Kenvetil on 2011-08-08
> **sikander3786 said:**
> Yeah need to see the outputs to find if your graphics card is actually capable of running Unity.
hey.. so i turned on the computer and the dual boot screen came up, with 5 options, like mentioned earlier.. de second one was called ubuntu, in Reocvery Mode os something like that.. i went into that, n a black screen with a lot of writings came up with large writings, den came another black screen with smaller writings.. i noticed it stalled at this command:
 
>  
[ 14.46534]Bad LUN (0:1)
[ 14.465481] Bad Target Number (1:0)
[ 14.465481] Bad Target Number (2:0)
[ 14.465481] Bad Target Number (3:0)
[ 14.465481] Bad Target Number (4:0)
[ 14.465481] Bad Target Number (5:0)
[ 14.465481] Bad Target Number (6:0)
[ 14.465481] Bad Target Number (7:0)

 
this was it.. there was no response from the computer until it was shut down
each time i mkae attempt to get into the recovery mode, this is what happened...
this didnot happen earlier wen i tried to get into the failsafeX mode.. i dunno wat to do now.. :(
 
a friend of mine is a member of ubuntu community, n they have developed Unity for them.. he says Unity has still not been tested with most graphic card, so suspect that shud be de reason.. if that helps..

---

### Post by sikander3786 on 2011-08-09
Your friend might be correct about Unity but your PC should at least be able to boot in recovery mode at least regardless of Unity.

And in situations like these when you are even unable to get to a recovery console, the only choice is to boot an Ubuntu Live CD/USB and either run a filesystem check or Chroot the install and try repairing it, the later of which requires some advanced skills.

In your case I would suggest a re-install, yet again.

Before that, following the steps below would ensure the cause of this inconvenience is not a corrupt ISO / bad burn. First, test your downloaded image for any possible corruption.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, burn it to a CD at the lowest possible speeds. If they don't match, re-download.'

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You can test the disk also when you boot it.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main](https://help.ubuntu.com/community/LiveCDBootOptions#Main) Page Options

Or you can also try burning it to a USB and then booting from it if your PC's Bios supports USB boot.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

---

### Post by OpenKOJU on 2011-08-09
I use HP-Pavilion g6-1037tx 
It has ATI-Radeon 6470 graphics card .
I installed ubuntu 11.04 in my system, it booted very for the first time and during another boot-up, the whole screen goes blank and it never shows up .
I tried installing again but the same problem .
Now I 'm using 10.10 which works fine except the error saying something like "graphics turbo disabled" in the startup

---

### Post by Nikhil Kenvetil on 2011-08-09
hey.. so i tried booting from de 11.04 cd, n to my uttermost disgust, it wasnt bootin into it.. i was still facin de no boot scenario (while bootin).. so i installed 10.04 in de same drive where 11.04 was installed, after wiping it out.. now i'd like to know if der is a way i can update 10.04 to 11.04.. plz help..

---

### Post by sikander3786 on 2011-08-11
I won't recommend upgrading to a version which doesn't work well at your PC. In fact, it is recommended to first boot a Live CD of the version you are upgrading to and test your hardware etc before you actually upgrade.

If you still want to do it, you can go to Software Center > Edit > Software Sources > Updates tab and under 'Release Upgrade', change 'Long term support release only' to 'Normal releases'.

Now from the Terminal:

```
sudo apt-get update && sudo apt-get upgrade
update-manager -d
```

Then you need to upgrade to 10.10 first and then 11.04 in two steps actually.

---

