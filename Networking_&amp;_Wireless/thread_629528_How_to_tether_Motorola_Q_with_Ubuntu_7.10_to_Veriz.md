---
title: "How to tether Motorola Q with Ubuntu 7.10 to Verizon"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by MasonSD on 2007-12-02
The last impediment for me to move from Vista to Linux is knowing how to tether my Motorola Q to Verizon in Gutsy Gibbon.  Currently, I am using PDANet, but it is not supported in Linux.

I have seen some similar posts on Google, but they are not very clear to me.  If anyone has this working, would you please provide clear instructions for a complete novice?  It looks like you have to modify a script in wvdial, but I haven't used a command-line prompt since I was typing "win" at C:\

In any event, I don't have an Ubuntu disc yet, so I want to be sure I'll have a hard copy before I format my hard drive and lose my internet access.

I am happy to use the USB cable for now but will probably want to try the Bluetooth connection down the road.

THANK YOU FOR CONVERTING ANOTHER PERSON AWAY FROM WINDOWS!!!

---

### Post by Jewfro_Macabbi on 2007-12-02
I have the same phone, and am trying to solve this issue also.

When wvdial first ran, did it identify for you which port your modem is on? something like /dev/tty/ACM0?

If you know this, then it's easy to set up wvdial.

from the terminal: sudo gedit /etc/wvdial.conf

for example - my wvdial.conf file w/my old phone looked like this:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = at+cgdcont=3,"IP","isp.cingular"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***3#
Password = CINGULAR1
Username = [email]ISP@CINGULARGPRS.COM[/email]


Make what changes you need, and save them.

Then to run it just issue wvdial from terminal.

---

### Post by MasonSD on 2007-12-16
Thanks!  But wvdial does not tell me what port my modem is on.

I can see a Motorola USB Remote NDIS Network Device in Device Manager, but have no idea what information to take from the Device Manager and enter into wvdial.conf.

I ran dmesg in the terminal, but instead of being informed of the port, I was told "usb 4-1: bad CDC descriptors".

HELP!  I can't get wvdial to find my phone!

---

### Post by ldrn on 2007-12-20
Hello;

If you're using PDAnet, the USB will not work. Bluetooth does, however. I hear "USB Modem" works with Linux on USB but not dial up, ironically... anyway, I use a program called WM5Storage so I can charge over USB without all the RAPI stuff.

The PDAnet channel changes; I use a small script to detect what it's currently using, but it's complicated. You need to know your device's bluetooth id thing (not the right term, I'm sure).  The way I did this was to use konqueror and type: 
bluetooth:/
into the address bar, then clicked on my phone's name after it found it. After you do this, the stuff in between "sdp://[" and "]/" in the address bar (no quotes) is the ID thing; it's hex, with : between every two characters. (Maybe it's the mac address?)

I find the channel like this, replacing 00:00:00:00:00:00 with the above number:
```
sdptool browse 00:00:00:00:00:00 | grep 'PdaNet Dial-up Networking' --after-context=8 | grep 'Channel' | cut -d ' ' -f 6

```
Let me know if this works for you or if you'd like more help. :)

---

### Post by lilbudda on 2008-01-03
Forgive my ignorance but I have been working on this ever since I got my phone. I do have PDANet installed and it works fine when I am in Windows. I would like to establish the connection via USB if possible but it always gives me a CHAP error after about 10 seconds. How do I create the Bluetooth network connection?

Thanks!

---

### Post by ldrn on 2008-01-04
OK! I'll do my best to help. This isn't the best way to do this, I'm sure, but it's the way I use... and I love the console in Linux and it's how I usually dial it, but I'll try to keep this GUI oriented.

I haven't gotten it to be able to tether over the USB connection -- it's faster than the bluetooth, by the way. I think USB Modem supports the Q -- they say they do -- but I haven't tried it.

For bluetooth, first you have to enable Bluetooth DUN in PDAnet on the phone. (Just run PDAnet on the Q and make sure the Bluetooth DUN box is checked.) Then you need that number I mentioned earlier. Install kbluetooth and konqueror (you can do this using the GUI package manager or application installer), then run kbluetooth and click the icon in the tray/notification area, and wait until it finds your phone. Double click on your phone, and take note of the number between [ and ] in the address bar -- that's your phone's Bluetooth ID, and you need it for the rest.

Edit /etc/bluetooth/rfcomm.conf using your preferred editor as root -- this would do it from the run dialog or command line if you have normal ubuntu installed:
```
gksudo gedit /etc/bluetooth/rfcomm.conf
```
Make it look like this, replacing "00:1A:00:00:1A:00" with that bluetooth ID I mentioned earlier.:
```

#
# RFCOMM configuration file.
#

rfcomm0 {
    # Automatically bind the device at startup
    bind yes;

    # Bluetooth address of the device
    device 00:1A:00:00:1A:00;

    # RFCOMM channel for the connection
    channel 0;

    # Description of the connection
    comment "MotoQ PDAnet";
}
rfcomm1 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 1;
        comment "MotoQ PDAnet";
}
rfcomm2 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 2;
        comment "MotoQ PDAnet";
}
rfcomm3 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 3;
        comment "MotoQ PDAnet";
}
rfcomm4 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 4;
        comment "MotoQ PDAnet";
}
rfcomm5 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 5;
        comment "MotoQ PDAnet";
}
rfcomm6 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 6;
        comment "MotoQ PDAnet";
}
rfcomm7 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 7;
        comment "MotoQ PDAnet";
}
rfcomm8 {
        bind yes;
        device 00:1A:00:00:1A:00;
        channel 8;
        comment "MotoQ PDAnet";
}

```



Next, edit /etc/wvdial.conf using your preferred editor as root -- this would do it from the command line or run dialog if you have normal ubuntu installed:
```
gksudo gedit /etc/wvdial.conf
```
Make it look like this (if you haven't edited it before, just replace everything:)
```

[Dialer Defaults]
Phone = #777
Username = blank
Password = blank
New PPPD = yes
Stupid Mode = yes
Baud = 15200
Dial Command = ATDT
Init2 = ATZ
Init3 = ATM0
FlowControl = crtscts
Modem Type = Analog Modem

[Dialer motoq]
Modem = /dev/rfcomm0

[Dialer motoq0]
Modem = /dev/rfcomm0

[Dialer motoq1]
Modem = /dev/rfcomm1

[Dialer motoq2]
Modem = /dev/rfcomm2

[Dialer motoq3]
Modem = /dev/rfcomm3

[Dialer motoq4]
Modem = /dev/rfcomm4

[Dialer motoq5]
Modem = /dev/rfcomm5

[Dialer motoq6]
Modem = /dev/rfcomm6

[Dialer motoq7]
Modem = /dev/rfcomm7

[Dialer motoq8]
Modem = /dev/rfcomm8

```

Ok, now things will get slightly more difficult... create a file named "dial-motoq.sh" in /usr/local/bin as root. From the command line, you could do this with:
```
gksudo gedit /usr/local/bin/dial-motoq.sh
```
Make it contain this, replacing 00:1A:00:00:1A:00 with your Bluetooth ID again:
```

#!/bin/bash
echo "Finding PDAnet Channel on MotoQ:"
CHAN=`sudo -H -u \#1000 sdptool browse 00:1A:00:00:1A:00 | grep 'PdaNet Dial-up Networking' --after-context=8 | gre
p 'Channel' | cut -d ' ' -f 6`
echo "Dialing channel $CHAN:"
sudo -H -u \#1000 wvdial motoq$CHAN

```
Save and close it, then make it executable like so, from the run dialog or the command line:
```
gksudo chmod a+x /usr/local/bin/dial-motoq.sh
```

Now you need to either restart your computer or enter this from the run dialog or the command line:
```
gksudo /etc/init.d/bluetooth restart
```

Ok, now you should be able to dial your modem from the command line by running "dial-motoq.sh". I have a GUI method for it as well -- if you'd like to use it, install "alltray" using apt-get or the package manager and download a good icon for it -- I use one of the Q I got somewhere and have it saved as /home/myname/bin/icons/motoq.png ; replace that in the following with whatever path you used -- then make a shortcut in your menu editor. I use KDE, so I right click the start menu and hit "Edit Menu", then "File>New Item" and made the name "Dial MotoQ Bluetooth", click the blank icon and select the icon the icon I mentioned, and the command (the important part):
```
alltray --no-alltray --show --icon /home/myname/bin/icons/motoq.png xterm -e /usr/local/bin/dial-motoq.sh
```
I also made sure "Enable Launch Feedback" was not clicked. I think on gnome, the procedure is similar, aside from the icon box having a spring thing instead of being blank to start and clicking a "new item" button instead.

Close the icon to disconnect. You many want to disable your Wifi connection first, too. I hope this works for you and isn't too confusing.

---

### Post by lilbudda on 2008-01-06
Sweet! That worked like a charm. Thank you very much!

---

### Post by ldrn on 2008-01-06
That's great! I'm really glad it worked. :D You're welcome!

---

### Post by merkel04 on 2008-05-22
Hello,

I have been trying to get this to work for a few hours, I keep getting this error:

Finding PDAnet Channel on MotoQ:
Dialing channel :
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory

If you could shed some light on how to fix this, that would be great!

(Ubuntu vr 8.04)

Thanks,
Brian

---

### Post by ldrn on 2008-05-22
Hey merkel04;

When you edited /etc/bluetooth/rfcomm.conf , did you make sure to replace 00:1A:00:00:1A:00 with your device's ID?

Also, after doing that, you might need to try:
sudo /etc/init.d/bluetooth restart

---

### Post by merkel04 on 2008-05-22
Double post sorry ;)

---

### Post by merkel04 on 2008-05-22
Well I had only put the first one. I just copy and pasted the entire file you posted, replacing every MAC ID with my phone's. Now I get,

```

Finding PDAnet Channel on MotoQ:
Dialing channel :
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: Invalid argument
--> Cannot open /dev/rfcomm0: Invalid argument
--> Cannot open /dev/rfcomm0: Invalid argument
brian@brian-laptop-ubuntu:~$ 

```


Any more help would be greatly appreciated.

Thanks again,
Brian

---

### Post by ldrn on 2008-05-22
Ouch... I have no idea what those ones could mean. :(  Double check your /etc/wvdial.conf... maybe?  I'd say to make sure it is running on your Q, too, but it sounds like it is from that.

---

### Post by merkel04 on 2008-05-27
hrmm well i double checked, then triple checked all of the files, they all seem to be correct. I guess ill keep playing around with it some more, if i find the solution ill post it up here.

Thanks for the help,
Brian

---

### Post by dark_harmonics on 2008-06-02
For those that want to use a USB connection check out the how-to here: [http://ubuntuforums.org/showthread.php?t=807893](http://ubuntuforums.org/showthread.php?t=807893)

---

### Post by dishguy123 on 2008-06-20
I'm having a similar problem.  The exact same error appears "cannot find /dev/rfcomm0: No such file or directory"  

Anyone with a solution?

Thanx....

---

### Post by fapestniedg on 2008-07-03
--> Cannot open /dev/rfcomm0: Invalid argument
--> Cannot open /dev/rfcomm0: Invalid argument
--> Cannot open /dev/rfcomm0: Invalid argument

sdptool reports my Moto-Q as "Dial-up Networking" not "PDANet Dial-up Networking" removing the PDANet from the regular expression in dial-motoq.sh cleared these errors for me.


```
#!/bin/bash
echo "Finding PDAnet Channel on MotoQ:"
CHAN=`sudo -H -u \#1000 sdptool browse 00:1C:12:78:31:F1 | grep 'Dial-up Networking' --after-context=8 | grep 'Channel' | cut -d ' ' -f 6`
echo "Dialing channel $CHAN:"
sudo -H -u \#1000 wvdial motoq$CHAN
```

---

