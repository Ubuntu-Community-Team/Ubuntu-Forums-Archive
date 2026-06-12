---
title: "Garmin Etrex Venture Cx + Ubuntu"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by simon0404 on 2010-05-09
I've recently switched over to Ubuntu, and I'm trying to get my GPS to  work with it......

I've got the Windows version of Firefox  running in Ubuntu, and I have the garmin communicator plugin for  geocaching.com.....

I get as far as opening the communicator  plugin, but my GPS is not detected, and I get the message "NO DEVICES  FOUND"..


Any help appreciated,
Thanks in advance,

Simon.

---

### Post by idef1x on 2010-05-27
I'm having the same with my etrex vista hcx. I didn't try out any linux programs yet, but most of them seem to work with serial devices and mine has USB.
Since I just got it yesterday I first wanted to know if everything worked so installed the windows software on a virtualbox windows 7 machine. That works fine.
Installing the software under Wine works too, but indeed no devices can be found. Mebe it needs an extra linux driver or so or it doesn't work at all...

---

### Post by fabio.hipolito on 2010-06-20
I have the same problem, cannot connect my garmin eTREX Venture Cx to my laptop because I only have Ubuntu

Does anyone have an idea? I have googled a bit but none of the solutions I found worked.

Best regards.

---

### Post by ocm_ott on 2010-07-05
> **fabio.hipolito said:**
> I have the same problem, cannot connect my garmin eTREX Venture Cx to my laptop because I only have Ubuntu

Does anyone have an idea? I have googled a bit but none of the solutions I found worked.

Best regards.

I use an eTrex Vista HCx

If you're a premium geocaching.com member, you might find programs like my own OCM ([http://sourceforge.net/projects/opencachemanage/](http://sourceforge.net/projects/opencachemanage/)), Cache 901 ([http://www.cache901.org/](http://www.cache901.org/)), or Geotoad ([http://code.google.com/p/geotoad/](http://code.google.com/p/geotoad/)) useful to manage or transfer caches to your device.

At a minimum, they all need gpsbabel (type "sudo apt-get install gpsbabel"). For most Ubuntu installations, before you can send things to your Etrex you have to create a file called " /etc/udev/rules.d/51-garmin.rules", with the value 'SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"', _Click _[here for more information.]("http://www.gpsbabel.org/os/Linux_Hotplug.html") Otherwise, only root can talk to your eTrex.

If you aren't using one of the above cache management programs, you'll need to save a .loc or .gpx to your ubuntu machine, and then send it to your etrex via gpsbabel by typing "gpsbabel -i <geo or gpx> -f <.loc or gpx> -o garmin -F usb:

i.e. gpsbabel -i geo -f geocaches.loc -o garmin -F usb:
or gpsbabel -i gpx -f mygpx.gpx -o garmin -F usb:

---

### Post by baddnady23 on 2010-07-05
I also have a garmin venture and after many tries, I got a program called Qlandkarte to work for transferring files to and from the GPS.  Check out this post here as it might help solve a problem you might be having:  [http://www.gpspassion.com/FORUMSEN/topic.asp?TOPIC_ID=121878]("http://www.gpspassion.com/FORUMSEN/topic.asp?TOPIC_ID=121878")

Also check out the wiki for JOSM  --->  [http://wiki.openstreetmap.org/wiki/JOSM]("http://wiki.openstreetmap.org/wiki/JOSM")

Search for the section on garmin and read up.  This helped immensely when using garmins and ubuntu together.

---

### Post by fabio.hipolito on 2010-07-30
> **ocm_ott said:**
> I use an eTrex Vista HCx

If you're a premium geocaching.com member, you might find programs like my own OCM ([http://sourceforge.net/projects/opencachemanage/](http://sourceforge.net/projects/opencachemanage/)), Cache 901 ([http://www.cache901.org/](http://www.cache901.org/)), or Geotoad ([http://code.google.com/p/geotoad/](http://code.google.com/p/geotoad/)) useful to manage or transfer caches to your device.

At a minimum, they all need gpsbabel (type "sudo apt-get install gpsbabel"). For most Ubuntu installations, before you can send things to your Etrex you have to create a file called " /etc/udev/rules.d/51-garmin.rules", with the value 'SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"', _Click _[here for more information.]("http://www.gpsbabel.org/os/Linux_Hotplug.html") Otherwise, only root can talk to your eTrex.

If you aren't using one of the above cache management programs, you'll need to save a .loc or .gpx to your ubuntu machine, and then send it to your etrex via gpsbabel by typing "gpsbabel -i <geo or gpx> -f <.loc or gpx> -o garmin -F usb:

i.e. gpsbabel -i geo -f geocaches.loc -o garmin -F usb:
or gpsbabel -i gpx -f mygpx.gpx -o garmin -F usb:
Hello to all,

now I can transfer files to my GPS via the command line. I try latter using the recommended software.

Thank you.

---

### Post by Spynexes on 2010-11-04
> **simon0404 said:**
> 
I've got the Windows version of Firefox  running in Ubuntu, and I have the garmin communicator plugin for  geocaching.com.....


You might want to try this:
[http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/)

in combination with gpsbabel. 
It is a firefox plugin that behaves like the original garmin communicator plugin. So you will be able to send geocaches to your garmin.

---

