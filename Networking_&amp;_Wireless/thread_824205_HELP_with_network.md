---
title: "HELP with network"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by wok951 on 2008-06-09
OK. I found this thing where i can set up a server and access my Ubuntu from anywhere on the web. It says i need to create a folder in /var/www but it won't let me. If anyone knows how to get around this thanks. Here is the website if you need it. Step #6. [http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)

---

### Post by Ayuthia on 2008-06-09
> **wok951 said:**
> OK. I found this thing where i can set up a server and access my Ubuntu from anywhere on the web. It says i need to create a folder in /var/www but it won't let me. If anyone knows how to get around this thanks. Here is the website if you need it. Step #6. [http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)
If you are trying to create a folder called remotecontrol in /var/www, then you need to do this at the Terminal:
```
sudo mkdir remotecontrol /var/www
```/var/www requires admin access because it affects webpages.

---

### Post by wok951 on 2008-06-09
ok. That created it in my home folder. I need it to go into the /var/www folder. I do i do that.

---

### Post by Ayuthia on 2008-06-09
> **wok951 said:**
> ok. That created it in my home folder. I need it to go into the /var/www folder. I do i do that.

I should double-check my work.  Sorry about that.  It should have read:
```
sudo mkdir /var/www/remotecontrol
```

---

### Post by wok951 on 2008-06-09
It worked thanks.

---

### Post by wok951 on 2008-06-09
OK Another problem. I get an error message when i try to extract.



error:  cannot create /var/www/remotecontrol/LICENCE.TXT
error:  cannot create /var/www/remotecontrol/WhatsNew
error:  cannot create /var/www/remotecontrol/ChangeLog
error:  cannot create /var/www/remotecontrol/README
error:  cannot create /var/www/remotecontrol/index.html
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncViewer.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/RfbProto.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/AuthPanel.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncCanvas.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncCanvas2.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/OptionsFrame.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ClipboardFrame.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ButtonPanel.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/DesCipher.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/CapabilityInfo.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/CapsContainer.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/RecordingFrame.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/SessionRecorder.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/SocketFactory.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/HTTPConnectSocketFactory.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/HTTPConnectSocket.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ReloginPanel.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/InStream.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/MemInStream.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ZlibInStream.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncViewer.jar.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/index.vnc.




Any Suggestions?

---

### Post by Ayuthia on 2008-06-09
> **wok951 said:**
> OK Another problem. I get an error message when i try to extract.



error:  cannot create /var/www/remotecontrol/LICENCE.TXT
error:  cannot create /var/www/remotecontrol/WhatsNew
error:  cannot create /var/www/remotecontrol/ChangeLog
error:  cannot create /var/www/remotecontrol/README
error:  cannot create /var/www/remotecontrol/index.html
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncViewer.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/RfbProto.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/AuthPanel.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncCanvas.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncCanvas2.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/OptionsFrame.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ClipboardFrame.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ButtonPanel.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/DesCipher.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/CapabilityInfo.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/CapsContainer.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/RecordingFrame.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/SessionRecorder.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/SocketFactory.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/HTTPConnectSocketFactory.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/HTTPConnectSocket.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ReloginPanel.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/InStream.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/MemInStream.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/ZlibInStream.class.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/VncViewer.jar.
checkdir error:  cannot create /var/www/remotecontrol/classes
                 unable to process classes/index.vnc.




Any Suggestions?

The problem is still with the permissions for that directory.  How are you extracting your .zip file?  If you are doing from Nautilus (from the GUI), then I would recommend trying this from the Terminal:
```
gksu file-roller
```You will then have to open the .zip file and then extract it to /var/www/remotecontrol.  Hope that helps.

---

### Post by wok951 on 2008-06-10
The program i am using is the archive manager. When i typed in the code it just gave me the same window. So in retrospect it didn't work. Any other suggestions? Thanks

---

### Post by Ayuthia on 2008-06-10
> **wok951 said:**
> The program i am using is the archive manager. When i typed in the code it just gave me the same window. So in retrospect it didn't work. Any other suggestions? ThanksSo did you try to extract the file and it failed?  The difference between the two is that the first time it was run without admin privilege and the second time was done with admin privilege (sudo).

---

### Post by Ayuthia on 2008-06-10
If the admin version did not allow you to extract, the other option to try is to change the permission of /var/www/remotecontrol so that you can put things in it and then change it back:
```
sudo chmod 766 /var/www/remotecontrol
```
Finish the guide then once you are done:
```
sudo chmod 755 /var/www/remotecontrol
```

---

### Post by wok951 on 2008-06-10
Ok. Thank you so much. I got it to work.

---

