---
title: "WUSB54G (Solution, not problem)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Jmtan on 2007-06-19
Hi, I just got my Linksys WUSB54G v4 working with my Ubuntu studio 7.04, and I thought I would post the method, as much for my future reference as anybody else's. :)

1. Grab latest ndiswrapper from their [site]("http://ndiswrapper.sourceforge.net/").
2. Untar, goto directory, "make distclean", "make", "sudo make install".
3. Grab latest driver from [linksys]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377540888B29&displaypage=download#versiondetail").
4. Unzip, find the WUSB54Gv4 directory.
5. Run "ndiswrapper -v", make sure no errors
6. "ndiswrapper -i rt2500usb.inf", "sudo depmod -a", "sudo modprobe ndiswrapper"
7. "ndiswrapper -l" may show an alternative driver (rt2570)
8. Blacklist the driver by running "sudo gedit /etc/modprobe.d/blacklist" and adding "blacklist rt2570" to the end.
9. "sudo gedit /etc/modprobe.d/ndiswrapper", change "wlan0" to "rausb1".
10. Reboot (prayer optional)

All this from memory, so may not be 100% accurate. I needed to do this to enable WPA2 support, although there was WEP support out of the box already.

---

### Post by squimito on 2007-07-02
THANK YOU!!!!!! That worked like a charm. When I first rebooted the WUSB54G did not want to power on and was not detected by Ubuntu. I rebooted a second time and it worked..hmm. It's working perfectly Jmtan, Thanks!!

---

### Post by be4truth on 2007-07-11
I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

---

### Post by roxattaq on 2007-07-27
Where did you get the "zip" file for WUSB54Gv4. On the linksys site there are only "exe" files. Another issue I'm having is when I run "ndiswrapper -v" I'm getting this message: Error: no versions of ndiswrapper found"
   I did download the the ndiswrapper-1.47 and and extracted the folder to my desktop but I'm stuck here. What's next???

---

### Post by fawazomr on 2007-07-27
I am newb on the Ubuntu 7.04. Can you please tel me the point #2 in expl. I realy do not know what are those dir. Please Help!!

---

### Post by Qinjuehang on 2007-10-09
For example your file is extracted in home/usrname
you will type cd home/usrname to go to that directory (in Terminal).
And thanks your your solution! A while back I was trying to get a Dapper Drake solution working in festy...and failed miserably.

---

### Post by mogedwards on 2007-10-09
Hi.

I'm the same as 'fawazomr', I don't understand #2 but I don't understand the reply by 'Qinjuehang' either.

Anybody help by giving directions for complete PC dumbo's like me. I literally need to be taken through it one step at a time.

Thanks

Mog

---

### Post by Qinjuehang on 2007-10-10
Extract the file to your home folder (using GUI)
type "cd /home/[your username]/[the folder you extracted it to]" (without quotes, the stuff in square brackets are to be replaced by the names of the folders)
continue on.

---

### Post by Qinjuehang on 2007-10-11
You forgot something! before #8, you need to use "ndiswrapper -m"

Posting this from ubuntu :D

---

