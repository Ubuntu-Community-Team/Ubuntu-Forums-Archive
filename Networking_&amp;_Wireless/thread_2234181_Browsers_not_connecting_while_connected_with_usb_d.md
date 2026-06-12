---
title: "Browsers not connecting while connected with usb data card (MTS)"
date: 2014-07-13
forum: Networking &amp; Wireless
---

### Post by Sandeep_Srivastava on 2014-07-13
I am using my MTS MBlaze usb data card to connect to internet. The data card is connecting properly as my torrent downloads are working and also the synaptic manager is able to download updates. But the problem is that none of my browsers including Galeon, Firefox and Konquerer are working and are showing as unable to connect to the internet.

---

### Post by varunendra on 2014-07-13
Welcome to the forums Sandeep! :)

Are you using the MBlaze application that comes with the device? If yes, there should be a button on its interface to open a browser. Click that to open a browser via the application itself, and if it is able to browse the internet, **[COLOR="#FF0000"]IMMEDIATELY CLOSE IT[/COLOR]** and post back here!

For reference on such behaviour, please refer to this post : [http://ubuntuforums.org/showthread.php?p=12945156#post12945156](http://ubuntuforums.org/showthread.php?p=12945156#post12945156)

More explanation later, if such behaviour indeed exists in your system too.

---

### Post by Sandeep_Srivastava on 2014-07-13
Hi Varun

Thanks a lot for your reply.

Yes, I am using the application which comes with the device but there is no button on its interface to open a browser. I have tried clicking all buttons which are there in the interface.

The thread which you posted the link to seems to be talking about a mobile parter application which appears to be a Huawei application, not sure how it can help in case of MTS application.
 
Thanks
Sandeep

---

### Post by varunendra on 2014-07-13
> **Sandeep_Srivastava said:**
> The thread which you posted the link to seems to be talking about a mobile parter application which appears to be a Huawei application, not sure how it can help in case of MTS application.

The point that I believe maybe common is that these applications tend to run the service as root, and so only those applications can access the internet that are run as root, including the browser. As such, a browser opened by the connection application itself can access the internet because it is run as root. But running a browser as root, as mentioned in the linked post, is a high security risk.

Can you post a screenshot of the MTS connection application? Or multiple ones if it has multiple tabs? I have only used its old windows version and that one did have a button somewhere to open a browser.

To test if my doubts/suspicion is correct, you may try to run a browser as root (be aware that it is risky, so close it as soon as it is confirmed that it can access the net). For example, for firefox -
Press "Alt-F2" > type "gksu firefox" > press 'Enter' (you may also run 'gksu firefox' from terminal instead of "Alt-F2", but then you'll have to keep the terminal open in background)

The package 'gksu' is not installed by default in Ubuntu 14.04, so you'll need to install it first before you can use it -
```
sudo apt-get install gksu
```

Why use 'gksu' instead of 'sudo' for GUI applications : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Sandeep_Srivastava on 2014-07-15
Hi Varun

Please find attached the MTS application screen. 

You are right about gksu. When I opened galeon browser using > gksu galeon I was able to browse just fine.

As you suggested that it is not safe to run browsers as root, what would you suggest in this case ?

---

### Post by varunendra on 2014-07-16
> **Sandeep_Srivastava said:**
> You are right about gksu. When I opened galeon browser using > gksu galeon I was able to browse just fine.

First of all, do you need to supply your login password when you run any command with 'sudo' ? I suspect not, which is what these kind of apps do when they get installed, and which I personally consider a height of folly and ignorance.

So if you no longer need to supply your login password when using 'sudo', that itself is another security risk, let's first patch it by reverting the change the MTS app might have made. Check your '/etc/sudoers' file (you need root access to even read it, so use sudo to read it) -
```
sudo cat /etc/sudoers
```
Do you see the following line -
```
ALL ALL=(ALL) NOPASSWD:ALL
```
..in the last?

If yes, disable it by commenting it out with the following command -
```
sudo sed -i '/NOPASSWD/ s/.*/# &/' /etc/sudoers
```
(assuming the offending line is the only one that contains the word "NOPASSWD").

You may confirm the change with the 'cat' command above. The line should now look like this -
```
**#** ALL ALL=(ALL) NOPASSWD:ALL
```

From now on, you should need to supply your login password whenever using 'sudo'. If yes, one security hole is patched.

Now to make internet connection accessible to normal user, I can think of two options at the moment (there can be more that might have skipped my mind) -

**1)** If you know or can determine the APN and dial no. (sometimes username and password too) of the MTS connection, you can configure the same in Network Manager itself to use it to connect to Internet. You will need to disable or completely uninstall the MTS application to be able to use the modem, since once claimed by the MTS app, it won't be available for NM.

**2)** Try closing the MTS application when it autostarts, then try running it as a normal user. For this you need to determine which program is run when you plug in the modem. The one I tested was a zte modem, and used "**/usr/local/bin/ztemtApp/bin/App**" program. So do you have this "/usr/local/bin/ztemtApp/bin/App" file? If yes, try running it normally (without sudo) -
```
/usr/local/bin/ztemtApp/bin/App
```
Does the application run? If yes, can you open a browser normally and browse the net now?

**PS:**
By the way, if I remember correctly, I think it is the second icon at the bottom of the screenshot you attached (the blue sphere) which provides the button to open a browser. Please confirm as this button may be needed if the application can be run normally, but a browser opened separately still can't browse the net.

---

