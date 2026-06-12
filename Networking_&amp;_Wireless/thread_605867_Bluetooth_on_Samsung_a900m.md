---
title: "Bluetooth on Samsung a900m"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by mjamesd on 2007-11-07
Since the Samsung a900(m) is a popular cell phone (at least in the US), I thought there would be a lot of information here about it.  However, that is not the case.

I am running Ubuntu Gutsy Gibbon (7.10), kernel v. 2.6.22-12-386 on a Dell Vostro 1500. I have gnome-obex-server, gnome-vfs-obexftp, bluetooth-analyzer, and btrcv (and all the basic bluez packages and libraries).  I can connect to, pair, and bond my phone (supported profiles: HSP, HFP, DUN, OPP,FTP,BPP) to my laptop (supported profile: OPP) using the bluetooth-analyzer icon in the system tray. I can browse my phone's "Exchange FTP Folder" using the same program. However, when I try to download files from my phone using my laptop, I have to click through a lot of "Are you sure?" type of notifications on my phone, even though I have my laptop set as a trusted source.  This isn't my main problem, but is anyone else having this problem?

My main problem is that I can't push files to my laptop using my phone. I have the option to send a picture I took with the phone's camera via bluetooth, but when I go to send the picture it asks "Do you want to search?" If I say yes, it searches for a while, finds whatever devices are in the area, but doesn't show any results. If I say no, it exits out to the phone's main menu without giving me the option of choosing the bluetooth device to which I want to send. This is an odd problem, but what makes it even more odd is that I *can* send "name cards" (basically, just a text file of a contact) from my phone to my laptop and it comes up on BTRCV as a received file. Doing it this way, I don't even have to tell it where to send; rather, the phone knows/decides where to send it and does so automatically (hopefully only to trusted devices!).

I tried using MultiSync but I don't think that this type of phone is supported. Are there plugins? I also tried using Wammu, but it kept crashing when I tried to connect to my phone. Here's a debug report:
> [Gammu            - 1.13.0 built 14:58:05 Oct  9 2007 using gcc 4.1]
[Connection       - ""]
[Connection index - 0]
[Model type       - ""]
[Device           - ""]
[Runing on        - Linux, kernel 2.6.22-12-386 (#1 Sun Sep 23 17:37:35 GMT 2007)]
Device 00:18:AF:16:77:0E ("MJAMESD")
   Channel 1 - "WBTEXT" (score=0)
   Channel 2 - "HSP Gateway" (score=0)
   Channel 3 - "HFP Gateway" (score=0)
   Channel 4 - "Dialup Networking" (score=0)
   Channel 5 - "Object Exchange" (score=0)
   Channel 6 - "File Transfer" (score=0)
Device 00:18:AF:16:77:0E ("MJAMESD")
   Channel 1 - "WBTEXT" (score=0)
   Channel 2 - "HSP Gateway" (score=0)
   Channel 3 - "HFP Gateway" (score=0)
   Channel 4 - "Dialup Networking" (score=0)
   Channel 5 - "Object Exchange" (score=0)
   Channel 6 - "File Transfer" (score=0)
Device 00:18:AF:16:77:0E ("MJAMESD")
   Channel 1 - "WBTEXT" (score=0)
   Channel 2 - "HSP Gateway" (score=0)
   Channel 3 - "HFP Gateway" (score=0)
   Channel 4 - "Dialup Networking" (score=0)
   Channel 5 - "Object Exchange" (score=0)
   Channel 6 - "File Transfer" (score=0)

I'm going to try [Mobile Phones on Linux]("http://ubuntuforums.org/showthread.php?p=1317977#post1317977") now. I'll post on how it turns out.

---

### Post by mjamesd on 2007-11-08
Well, it didn't support my phone... still no luck. I couldn't find anything online about supporting the FTP Bluetooth profile on Linux/Ubuntu. Any suggestions?

---

### Post by Phurter on 2007-11-29
I'm in the same boat. I've tried using obexftp to get a file from my phone (A900) and it fails. I can list the contents of the pictures folder, but I can't download them.

```

 <file name="SSPX0192.jpg" size="248179" user-perm="R"/>
 <file name="SSPX0197.jpg" size="565172" user-perm="R"/>
</folder-listing>done
Disconnecting...done
prompt:~$ obexftp -b xx:xx:xx:xx:xx:xx -c / -g SSPX0197.jpg -v
Browsing xx:xx:xx:xx:xx:xx ...
Channel: 6
Connecting...done
Sending ""... done
Receiving "SSPX0197.jpg"... failed: SSPX0197.jpg
Disconnecting...done

```

---

### Post by mjamesd on 2008-02-21
Yeah, I get the same thing. Very odd. I haven't worked on this problem in a while. I have my FTP exchange folder on the phone set to the folder that has my pictures in it, but it won't transfer them. Just like your output, it... wait, whoa!!!!!! It just worked!

I did just what you did, with my phone open. The phone asked me if I wanted to receive a file, I said yes, then it transfered the picture from my phone to my laptop! Victory!

```

user@localhost:~$ obexftp -b xx:xx:xx:xx:xx:xx -c / -g SSPX2088.jpg
Browsing xx:xx:xx:xx:xx:xx ...
Channel: 6
Connecting...done
Sending ""... done
Receiving "SSPX2088.jpg"...\done
Disconnecting...done
user@localhsot:~$ ls
SSPX2088.jpg

```

Sweet, I'll look into this more. Thanks for that command, by the way. I hope it works for you.

---

### Post by mjamesd on 2008-02-21
Yeah, you have to have the phone open and agree to file transfers on the phone, but then it'll work! I  right-clicked on the Bluetooth Manager icon in the system tray, selected 'Browse Device...', clicked my phone, clicked 'Connect', it opened Nautilus with the file viewer. I could open pictures and copy pictures to my laptop, but every time I did anything the phone asked me to allow it.

When I try to transfer files from my laptop to my phone using Nautilus, it doesn't work. But using obexftp, it does work. Same as what you did, but use -p instead of -g
```

vvgogh@amsterdam:~$ obexftp -b xx:xx:xx:xx:xx:xx -c / -p SSPX2089.jpg
Browsing  xx:xx:xx:xx:xx:xx ...
Channel: 6
Connecting...done
Sending ""... done
Sending "SSPX2089.jpg".../done
Disconnecting...done

```

The phone asks for confirmation, then it transfers it. But in Nautilus, it won't work. First, I tried just dragging and dropping from one Nautilus window to another. It looks like it's going to work, then says that the file is too large. When I right-click on the file and click "Send to..." then select "Bluetooth (OBEX Push)" for "Send as" and the click okay and it does nothing! The file doesn't show up in the other Nautlius window or in the FIle Manager on the phone.

So now that I've found out how to transfer files back and forth (using obexftp from the terminal), now I need to figure out how to do it without the phone asking for confirmation every time I do anything.

---

### Post by mjamesd on 2008-04-10
i wrote a couple bash scripts to do this easier. sorry... i'm not very good at bash. the first argument is your phone's bluetooth address and the second argument is the file you wish to send/receive. it puts the received file in the current directory and puts the sent file in the root "ftp" directory.

---

### Post by agibby5 on 2008-06-26
I'm trying to do this as well but can't even connect. 

```
andy@m1330:~$ obexftp -b 00:16:DB:58:8D:BB -c / -p SSPX0041.jpg -v
Browsing 00:16:DB:58:8D:BB ...
Channel: 6
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
andy@m1330:~$ 

```

I think I'm  using the right channel.... Result of > sdptool browse 00:16:DB:58:8D:BB 
```


Service Name: Object Exchange
Service RecHandle: 0x10004
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 5
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: File Transfer
Service RecHandle: 0x10005
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    **Channel: 6**
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

```

---

### Post by mjamesd on 2008-06-30
Yes, channel 6 is right. Can you connect using the bluetooth applet? Also try the Blueman Bluetooth Manager. I haven't had any luck transfering files with either program (or Nautilus, either), but at least you'll be able to see if you can connect to your phone.

Other than that... do you have your phone open and are you accepting the connection?

---

