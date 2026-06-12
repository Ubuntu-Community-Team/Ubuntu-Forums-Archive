---
title: "Still trying to install SKYPE on 11.04"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by L Campbell on 2011-08-15
I have tried these methods but without success:-

32 bit
wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
sudo dpkg -i getskype-linux-beta-ubuntu-32
sudo apt-get -f install


sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
cd / tmp wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
cd / tmp wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
sudo dpkg-i skype-*. Deb
sudo apt-get -f install


#2 : Install skype – either by ‘Right Click -> Open with Ubuntu Software Center ->Install’ method or from command line using dpkg, Type the following command(s), followed by your user account password (Here I assume your computer architecture is 32 bit, if you have other package, then just change the command according to that):
sudo dpkg -i skype-ubuntu_2.2.0.25-1_i386.deb
#3 : Wait, until the installation is complete. That’s all..access it from Main Menu (Top Left) or pinch it to the left icon panel (as a launcher), if you use it frequently.

I know that my microphone/headset functions because I've used it with SKYPE on my machine that has 10.04.3.

Your suggestions will be appreciated.

---

### Post by Daveth on 2011-08-15
so, is it installing, but not working, or not installing at all?

---

### Post by flyfishingphil on 2011-08-15
> **L Campbell said:**
> I have tried these methods but without success:-

32 bit
wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
sudo dpkg -i getskype-linux-beta-ubuntu-32
sudo apt-get -f install


sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
cd / tmp wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
cd / tmp wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
sudo dpkg-i skype-*. Deb
sudo apt-get -f install


#2 : Install skype – either by ‘Right Click -> Open with Ubuntu Software Center ->Install’ method or from command line using dpkg, Type the following command(s), followed by your user account password (Here I assume your computer architecture is 32 bit, if you have other package, then just change the command according to that):
sudo dpkg -i skype-ubuntu_2.2.0.25-1_i386.deb
#3 : Wait, until the installation is complete. That’s all..access it from Main Menu (Top Left) or pinch it to the left icon panel (as a launcher), if you use it frequently.

I know that my microphone/headset functions because I've used it with SKYPE on my machine that has 10.04.3.

Your suggestions will be appreciated.
LC, I put Skype on my 11.04 yesterday. Using the methods you described above. Didn't work at all so I removed it, went into Software Center, entered Skype in search and it brought up version 2.2.0.35-0natty1 and installed from there. 2nd time worked like a charm and it works just fine. 

Only problem noted so far, and it's on Skype, Sound Recorder and any other sound trials I've done, the Logitech Clear Choice headphone/mic setup is barely audible and it doesn't seem to provide much more than a whisper on input. Volume at max on computer so have no idea what/why it's not working as it did in 10.04.

Might try the remove and reinstall the way I did and see if that changes how well it works. Hope this helps and works for you too.

---

### Post by L Campbell on 2011-08-16
> **Daveth said:**
> so, is it installing, but not working, or not installing at all?

Sorry, I should have been more explicit here.

It installed (2.2.0.35-1) in Synaptic and also Applications > Internet but fails the 'test call'.

---

### Post by L Campbell on 2011-08-16
> **flyfishingphil said:**
> LC, I put Skype on my 11.04 yesterday. Using the methods you described above. Didn't work at all so I removed it, went into Software Center, entered Skype in search and it brought up version 2.2.0.35-0natty1 and installed from there. 2nd time worked like a charm and it works just fine. 

Only problem noted so far, and it's on Skype, Sound Recorder and any other sound trials I've done, the Logitech Clear Choice headphone/mic setup is barely audible and it doesn't seem to provide much more than a whisper on input. Volume at max on computer so have no idea what/why it's not working as it did in 10.04.

Might try the remove and reinstall the way I did and see if that changes how well it works. Hope this helps and works for you too.

Thanks very much for the help.

In Software Center I had 7 choices, none of which showed '0natty1', so I just clicked on the option with the '**S**' in a blue circle.

After installation it appeared in Synaptic as ' 2.2.0.35-0Lucid1 ' and is now working perfectly.

---

