---
title: "Installing Edubuntu on a Wubi Ubuntu 10.10 without internet access"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by MephistoM on 2010-11-06
Hello everyone,

I'm trying to get Edubuntu and some other software into remote schools - however, these schools have no internet connection whatsoever.  The teacher wishes to try to use wubi (because it's easy to uninstall it from windows if she doesn't like it) to install ubuntu 10.10 and then install the Edubuntu software package and related educational programs on top, such as Ofris.  My questions are:

- is there a way to install the edubuntu package on top of a wubi ubuntu 10.10 without an internet connection?
- does the latest wubi work with an edubuntu 10.10 iso in an offline setting?  

Many thanks.  I'm a few months into ubuntu myself, and I really wanted to help the school out.

---

### Post by Hippytaff on 2010-11-06
Do you think it would be possible to boot from CD or usb to try it...I think wubi only does the full ubuntu install then you have to install the edubuntu stuff (which doesn't seem to be an option if the school pcs are not online)

---

### Post by bcbc on 2010-11-06
You should be able to update to edubuntu as described [here]("https://help.ubuntu.com/community/InstallingSoftware#Use the Synaptic package download script").

> Use the Synaptic package download script
Here's how: Synaptic/PackageDownloadScript

Short instructions:

Launch Synaptic on the offline computer
Mark the packages you wish to install
Select File->Generate package download script
Save the script to your USB key
Take the USB key to an online Linux computer and run the script there from the USB key. It will download only the packages required by the offline computer to the USB key.
Insert the USB key into the offline computer
Launch Synaptic and click on File->Add downloaded packages
Select the directory on your USB key containing the downloaded *.deb files and press Open. The packages will be installed.

---

### Post by MephistoM on 2010-11-07
Thank you very much for your replies, they were extremely helpful.  I was able to install edubuntu on the ubuntu wubi without internet!  

Just for documentation and assistance for others who might have the same problems, here's what I did:
-> Launch synaptic from system -> administration -> synaptic package manager. 
-> click "status"
-> search Edubuntu
-> click "edubuntu-desktop".  Follow the prompts when it wants to include other software (the software within edubuntu).
-> select file -> generate package download script.  Save the script to a usb.  
-> find a ubuntu computer that has good internet.  plug in the usb and run the script (you saved it with a name) and grab a coffee while the download occurs.  
-> once it's done, go to your offline computer.  Launch synaptic.  Click File-> Add downloaded packages.  Go to the USB drive.  Click "open" despite the deb files being in grey (and that you can't select them).  Ubuntu will ask you if you wish to install the package and apply changes, click apply.  Let the installation happen, and you have your ubuntu/edubuntu on wubi w/o internet!  

Thanks so much for your continued help.    Now my question is - do you follow the same steps regarding any program on the ubuntu software center (for example, another educational program or game?)

---

### Post by bcbc on 2010-11-07
Everything on software centre should be available on synaptic. So you would just identify what you want, and follow the same steps as you did to install edubuntu.

If you know what you want you can probably include all the games etc. along with edubuntu-desktop and do it all at the same time.

---

### Post by MephistoM on 2010-11-07
Sorry - one additional problem came up.  When installing some programs via this method, such as adobe flash, this error message comes up:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.2-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.2-3_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmng/libmng1_1.0.9-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmng/libmng1_1.0.9-1ubuntu1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-6ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-6ubuntu2_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.4.2-0ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.4.2-0ubuntu4_all.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-5_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-webkit_4.6.2-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-webkit_4.6.2-0ubuntu5.1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


Is there a way to resolve this?

Many thanks!

---

### Post by bcbc on 2010-11-07
> **MephistoM said:**
> Sorry - one additional problem came up.  When installing some programs via this method, such as adobe flash, this error message comes up:

...

I don't know what the problem is. But when I click on those links I get the downloaded .deb, so not sure why it wouldn't work for you.

---

### Post by MephistoM on 2010-11-07
That is really strange - doesn't the procedure above download all the necessary files for installation?  When I try to install adobe flash on the offline edubuntu computer, how do I make sure that synaptic gets ALL the necessary deb files so that i can import it and download it from the online computer?  

Many thanks again, sorry for the additional questions.

---

