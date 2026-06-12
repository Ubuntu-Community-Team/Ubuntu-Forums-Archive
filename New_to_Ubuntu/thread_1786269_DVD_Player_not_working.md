---
title: "DVD Player not working"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by mattygee on 2011-06-19
Hi 

I have been trying to watch DVDs on my laptop with ubutntu 11.04. Whenever I load a disk it is not readable: error messages come up saying that no decryption software is installed, or that it doesn't have the correct plug in. When I look for plug ins and decryption software I cannot  find any available to download.

I tried to find other players, but none seem work.

Any ideas how I get my dvd player working again following my recent switch to ubuntu?

Many thanks

---

### Post by wolfen69 on 2011-06-19
```
sudo apt-get install libdvdread4
```
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
enjoy your movies.

---

### Post by subchief on 2011-06-19
Have you installed the required codecs via synaptic package manager? If not the do so and try to play the dvd again.

---

### Post by mattygee on 2011-06-19
> **subchief said:**
> Have you installed the required codecs via synaptic package manager? 

I am afraid that comment looks like a foreign language to me....you do need to bare with me as I know nothing about linux. Until now I have used macs all my life and never done any programming whatsoever.However.....

I tried this in the terminal:
sudo apt-get install vlc && \
> sudo apt-get install libdvdread4 && \
> sudo /usr/share/doc/libdvdread4/install-css.sh

...still didnt work came up as

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Is "root" my computer? 

Any idiot-proof suggestions as to how I sort this would be appreciated.

thanks.

---

### Post by mattygee on 2011-06-19
After reading other forums, I also tried changing the DVD region setting back to zone 2 as it was with windows. But when I typed into a terminal:

sudo regionset

I was just told "command not found"......

---

### Post by wildmanne39 on 2011-06-19
> **mattygee said:**
> After reading other forums, I also tried changing the DVD region setting back to zone 2 as it was with windows. But when I typed into a terminal:

sudo regionset

I was just told "command not found"......
Hi, first you can only have one instance of an installer program open at a time make sure if the terminal is open that the software center or synaptic is closed. Next when you run the commands in post #2 enter your password after you enter the first command it, will not show it on the screen when you type but it will wait until you enter it.

---

### Post by subchief on 2011-06-20
> **mattygee said:**
> I am afraid that comment looks like a foreign language to me....you do need to bare with me as I know nothing about linux. Until now I have used macs all my life and never done any programming whatsoever.However.....

I tried this in the terminal:
sudo apt-get install vlc && \
> sudo apt-get install libdvdread4 && \
> sudo /usr/share/doc/libdvdread4/install-css.sh

...still didnt work came up as

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Is "root" my computer? 

Any idiot-proof suggestions as to how I sort this would be appreciated.

thanks.

Ok,lemmi give it another go...
close any open windows and applications
-click on the ubuntu button on the top left corner and type synaptic.this will display an application called synaptic package manager.
-click to open that app.enter your adnin pasword when prompted.
-once the app is running,type libdvdread in the searchbox.several app wil be displayed.
-locate dvdread4 and click the checkbox and mark for intallation.
-also type in the searchbox gstreamer0.10 and check the plugins that are displayed.i sugest u select the gstreamer plugins with ugly in the file name.
-next,click on the tick on the menu bar that says apply changes.
-click ok or next on the dialogbox that appears.
-now wait till the installation is done then try to play your dvd.

hope that works!
cheers!

---

### Post by mattygee on 2011-06-20
Thanks for all your help. I have done all the suggestions, and was hopeful that it would work as all appeared to be there and i successfully changed the region code.... BUT still coming up with:

"could not read DVD. this may be because dvd decryption library is not installed"

... seems so complicated for what is usually such an easy function of a computer?

---

### Post by subchief on 2011-06-20
Hey try this links, They should give you more info and help sort  out your current predicament.

[http://ubuntuforums.org/showthread.php?t=1737727](http://ubuntuforums.org/showthread.php?t=1737727)

[http://ubuntuforums.org/showthread.php?t=584384](http://ubuntuforums.org/showthread.php?t=584384)

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/)

If the links don't work just copy and paste the address in your browser and you are good to go!
cheers!!

---

### Post by mattygee on 2011-06-21
:popcorn::popcorn::popcorn:

Thanks Subchief. Finally I have a working DVD player. 

For others consulting this thread for their own troubles, this is what worked in the end... typing this into terminal(for 64 bit laptop):

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

However can't say if that was all, you may have to follow all the instructions on this thread.

Thanks again everybody.

---

### Post by wildmanne39 on 2011-06-21
> **mattygee said:**
> :popcorn::popcorn::popcorn:

Thanks Subchief. Finally I have a working DVD player. 

For others consulting this thread for their own troubles, this is what worked in the end... typing this into terminal(for 64 bit laptop):

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

However can't say if that was all, you may have to follow all the instructions on this thread.

Thanks again everybody.would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by m666 on 2011-06-24
> **wolfen69 said:**
> ```
sudo apt-get install libdvdread4
```
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
enjoy your movies.

Thaaaaaanxxxxx!!!!!

---

