---
title: "set wireless rate automatically"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by cc_humbry on 2008-06-02
Hi, 
I have recently upgraded my laptop to Hardy via the update manager and since then my maximum wireless rate is only 1MB as reported via iwconfig.
I can set this to be higher by sudo iwconfig wlan0 rate 54M which works OK and all is fine and dandy. However I don't know how to get this to 'stick' following a reboot.

I am using fluxbox as WM in order to get a bit more out of my laptop resources (in fact I have the same problem above using Gnome), but I am using nm-applet in the fluxbox apps file to start network manager. This is fine and all wireless connections (my neighbours included) are shown in the list. OK so fine, I have tried using wireless-rate 54M in /etc/network/interfaces but I believe as I am using nm-applet this doesn't actually get used. It certainly doesn't appear to pick up this setting anyway as iwconfig still shows 1MB. There is no other settings in my interfaces file other than 
auto lo 
iface lo inet loopback
so I believe the only way wireless is being connected is via nm-applet.

Question is then - how do I either set rate to be 54M in networkmanager (nm-applet) automatically or how do I set it automatically using iwconfig and the interfaces config file????

Wireless works absolutely fine with the way it is set up other than I can't get the max speed to be set automatically. This only has changed following update to 8.04 (which is pretty annoying).

Thanks
Conrad

---

### Post by cc_humbry on 2008-06-03
is this really that difficult?
Anyone help as I have tried all I can think of. I am a newbie at this really. 
Do I have to write some sort of script to run at startup - would have thought it should be done using e either nm-applet or iwconfig. I tried using a more hard coded approach using interfaces config file and stopping nm-applet, but that didn't work either. Don't really understand how iwconfig stuff is invoked other than on the command line.
Thanks
Conrad

---

### Post by kolemik on 2009-01-20
Problem can be solved in the file:
/etc/NetworkManager/dispatcher.d/01ifupdown

This script called everytime you connect to network (wired or not).
My script has this code in "pre-up" section:
```

    pre-up)
        export MODE="start"
        export PHASE="pre-up"
        if test "$1" = "wlan1"; # Check that interface is wireless
        then
                # Set WIFI rate to 54;
                /sbin/iwconfig "$1" rate 54M
        fi;
        exec run-parts /etc/network/if-pre-up.d
        ;;

```

Note! You must set rate before interface is really up:```
exec run-parts /etc/network/if-pre-up.d
```

---

### Post by brewerdave on 2009-01-23
Hi,as a very "newbie" with the same problem I tried to edit the file to include the modified lines to preset the rate to 54 Mb;I can't save the file however,it tells me I don't have permission.How do I get round this?

---

### Post by Sava8420 on 2009-01-23
> **brewerdave said:**
> Hi,as a very "newbie" with the same problem I tried to edit the file to include the modified lines to preset the rate to 54 Mb;I can't save the file however,it tells me I don't have permission.How do I get round this?

Ok first off if you are just point and clicking your way to the file then no you will not be able to save.  The way around this is by opening a terminal window applications <accessories <terminal then in terminal type: 
```
nautilus
```
It will prompt you for password so type it in.(note the cursor will not show your typing of password)  Hit enter and it should open up your home folder.  Keep the terminal window open and navigate to location of file and insert your changes.  Save and all should work.  Or go to terminal and insert:
```
sudo gedit filename
```
Enter your password and of course replace "filename" with whatever file you are trying to edit.  This should open the specific file you can make your changes and save file.  In both of these ways you are elevating your user privileges to a "root" user.  Good luck.

---

### Post by brewerdave on 2009-01-23
Thanks very much for the help Sava8420 -it worked in so far as I've saved the modified file as listed by kolemik.
However, it hasn't achieved the primary objective; my network connection stays at 1Mb/sec after a restart!!!!
So I'm stuck with using sudo iwconfig..... every time I start up to get the full rate wireless connection. I'll continue to research!!!:(

---

### Post by richdf on 2009-06-27
Just run a fresh install of 9.04 & needed to auto configure rate as above. @brewerdave, Just an observation, but the script above sets rate to wlan1. My wifi is wlan0. This can be confirmed via a terminal with iwconfig (no switches) to list all wireless connections. 
Thanks to kolemik for this fix - better than other suggestions I have tried IMHO!

---

### Post by cc_humbry on 2009-06-28
another fix that seems to work (just installed Mythbuntu 9.04 and the problem still exists so not fixed in 9.04 - for me anyway)

add 
iwconfig wlan0 rate 54M
to 
/etc/rc.local

(or whatever your wireless is shown as instead of wlan0)

This worked for me.

---

