---
title: "Bluetooth Dial-up Networking"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by A. J. Rimmer on 2007-08-27
Bluetooth Dial-up Networking

I'm not sure how many people will find this applicable, but since I have been through this process three or four times and think I finally have it down pat, I thought I would post what I have learned for the possible benefit of others.

This describes the setup of dial-up networking using a USB-to-Bluetooth adapter and a Bluetooth modem.  This should also be applicable for those who use a Bluetooth-enabled telephone for Internet access, although you will probably need to create an additional chatscript or two (which you should be able to find elsewhere on the Internet).  This whole process was discussed in Ubuntu Hacks (O'Reilly) as it pertains to Dapper, but changes in Feisty have made it a lot simpler, I believe.  (Or maybe it just appears that way to me because I have struggled through it so many times over a period of many months.)

Here goes...

1. Install Bluetooth File Sharing using the Add/Remove function under Applications.  Among other things, this installs the Gnome Bluetooth Manager.  Open Bluetooth Preferences (under the System / Preferences menu) and select "Always display icon" or "Only display when adapter present" under the General tab.  I found that I had to do a restart of the computer at this point to get the Bluetooth icon to appear in the Top Panel (see #3, below).

2. Open the /var/lib/bluetooth folder.  This will enable you to monitor progress as you proceed through this procedure.

3. Connect you Bluetooth adapter and note that the Bluetooth icon appears in the Top Panel.  You should see that a folder is created in /var/lib/bluetooth.  This folder will be named after the mac address of your adapter.  Open this folder and keep it open; there should be a file named "config" at this point.

4. In a terminal, run hcitool scan.  This will give you the mac address of your modem, and will create files named "classes", "lastseen", and "names" in /var/lib/bluetooth/"mac_address".

5. Modify the /etc/bluetooth/rfcomm.comf file as follows using Root privileges.  (Press Alt-F2 and enter gksudo gedit to get started, then open the file for editing.)  Here is what mine looks like (substitute your own modem's mac address after the word "device" -- NB, this is the modem's mac address, not the adapter's address!):

#
# RFCOMM configuration file.
#
 rfcomm0 {
   bind yes;
	# Bluetooth address of the device
	device 00:00:00:00:00:00;
	# RFCOMM channel for the connection
	channel	1;
	# Description of the connection
	comment "Bluetooth Modem";
}

6. In a terminal, enter sudo killall -HUP hcid.  This "hangs up" and restarts the Bluetooth Host Controller Interface Daemon.  Then enter sudo rfcomm bind rfcomm0.  This binds the rfcomm device to the remote Bluetooth device.  (Enter info hcid and/or info rfcomm in a terminal to learn more about this.)

7. Now, set up the dial-up networking parameters.  You can do this in one of at least two ways.  I think the easiest is to click the Networking icon in the Top Panel, select Manual Configuration, Select Modem connection, click Properties, and enter the appropriate information.  Set the modem port to /dev/rfcomm0.  You can also use sudo pppconfig in a terminal to set up dial-up networking, then use pon, plog, and poff in a terminal to control the connection.  (Use info pppconfig, etc. if you have any questions.)

8.  Initiate the dial-up connection using pon or by clicking the Network icon then selecting Dial Up connections and then Connect to ppp0 via Modem.

9. A balloon should appear at the Bluetooth icon requesting pairing information.  Enter the access code for your modem, and the connection should proceed.  Once pairing is established, note that "linkkeys", "lastused", "features", and "manufacturers" files are created in /var/lib/bluetooth/"mac_address".

10. You can monitor the progress of the Bluetooth and dial-up connection by entering tail -f /var/log/syslog in a terminal before you start the connection process.  This will display a running account of the last ten lines of the System Log and will show the running dialog between your computer and the modem.  (Enter Ctrl-C to terminate the log display.)  You will probably see an error message stating "Couldn't activate dialup device ppp0 via Modem (ppp0)"; I don't know why this appears and it doesn't seem to affect anything.

11. If your particular application needs a custom chatscript, you can easily modify /etc/chatscripts/ppp0 (if you use the Network icon to initiate dial-up networking) or /etc/chatscripts/provider (if you use pon).  One thing I did was to change ATDT to ATM0DT, which turns off the modem speaker, which is just a personal preference.  Since my modem is in a completely different building, I use the System Log to verify that the connection process is going OK. 

12. One last thing you can do is add a Network Monitor icon to the Top Panel, then set it to ppp0 once your connection is established.  This will let you see when the connection is established and when it is disconnected.

---

### Post by s5GbJReJ on 2008-02-23
Thank you! I found this on Google and it seems like I should be able to get DUN working with my phone now :)

---

### Post by JacquiOh on 2008-05-01
Hi, I know this is an old post but I'm trying to get my bluetooth modem working on Hardy and I came across this on Google. 

Everything went ok until I tried to activate the connection, but this is what I get when I try to monitor the connection.

Does anyone have any ideas?

Thanks!

> May  1 22:53:02 jacqui-laptop pppd[14827]: Using interface ppp0
May  1 22:53:02 jacqui-laptop pppd[14827]: Connect: ppp0 <--> /dev/rfcomm0
May  1 22:53:02 jacqui-laptop pppd[14827]: Hangup (SIGHUP)
May  1 22:53:02 jacqui-laptop pppd[14827]: Modem hangup
May  1 22:53:02 jacqui-laptop pppd[14827]: Connection terminated.


---

### Post by ubuntuB on 2008-05-01
I had this working in 7.10 , I upgraded to 8.04 and was unable to connect to the internet via bluetooth DUN blackberry connection. I tried a fresh install to no avail. Im basically using this configuration:
[http://www.artficial.com/2008/01/howto_tether_a_blackberry_8830.html]("http://www.artficial.com/2008/01/howto_tether_a_blackberry_8830.html")

The script runs, I see modem mode enabled on the BB for a brief second and the connection fails.

I do not remember where, but I saw a post on another forum where someone else is having issues with 8.04 and Bluetooth DUN.

If I find a solution, I will post.

---

### Post by JacquiOh on 2008-05-01
Thanks for replying and letting me know... I hadn't tried to connect in 7.10 so it's useful to know there's a difference. 

My connection works perfectly in Windows, so it pains me that I have to use Windows unless there's a wireless network around.

I'll post as well if I figure it out! :-)

---

### Post by A. J. Rimmer on 2008-05-01
I haven't been using Bluetooth lately.  I can't recall if the "connect" message means that the computer has connected with the modem via Bluetooth, or if the modem has connected with the host.  Obviously then something is making the modem hang up.  The hangup could be caused by failing to send the proper user ID and/or password, so you might take a look at how you have that set up.

Best of luck.  I am still using Feisty here, as I have too been busy to work on upgrading.

---

### Post by ubuntuB on 2008-05-07
Well, im back to playing World of Warcraft on Ubuntu via bluetooth connection to my blackberry while driving down the interstate and having a cold one. I wish that I could tell you that I found a cool workaround, but I changed nothing! I suspect the issue was resolved in one of the latest round of updates.

Anyway, 8.04 now has the seal of approval for Bluetooth Blackberry DUN

P.S. I was just kidding, DO NOT USE YOUR COMPUTER WHILE DRIVING! I was once ran off the road by a patrol car, because the officer was playing with his laptop. Nearly spilled my cold one. psst, Im kidding about that too, dont get all bent out of shape.

---

### Post by JacquiOh on 2008-05-09
Hm, I'll have to have another go at it I guess! My system's all updated but still I can't get anything working.

---

### Post by gangalee on 2008-05-20
I've been able to get my Blackjack I with WinMo6 going with Internet Connection Sharing (although it seems to block me from the USB connection with my existing working wvdial.conf) from [http://www.howardforums.com/showpost.php?p=10356202&postcount=23]("http://www.howardforums.com/showpost.php?p=10356202&postcount=23")

but I'm getting the dreaded "[ 3926.496000] rfcomm_tty_ioctl: TIOCGSERIAL is not supported" error[http://www.google.com.jm/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=Urt&q=rfcomm_tty_ioctl%3A+TIOCGSERIAL+is+not+supported&btnG=Search]("http://www.google.com/search?hl=rfcomm_tty_ioctl%3A+TIOCGSERIAL+is+not+supported&btnG=Search") , the best link seems to be the one in Deutsch, but since that was the one class I ever flunked beside art (wine+women:guitar:), I can't figure out how to get a good wvdial.conf.

Can you suggest anything for us wvdial users?

---

