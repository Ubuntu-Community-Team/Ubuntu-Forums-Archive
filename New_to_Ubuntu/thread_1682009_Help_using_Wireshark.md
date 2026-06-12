---
title: "Help using Wireshark"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by suomalainen on 2011-02-05
Ubunteros,

I was recently pointed to a tool called WIRESHARK.

What I want to be able to do is match the Skype "localtime" of the person I'm having a chat with (info is in their Skype profile) to the actual physical location of the IP address they are using.

SIDE NOTE: Local time setting in Skype is based on how a person has constructed their profile. True/False? Something to keep in mind?

In some respect you can think of this as verifying a persons "caller i.d.". On the other hand, if a family member tells you they need $500 bucks for a trip to Texas but instead they are partying away in NYC... Well you figure it out....

So I read the Users guide for WIRESHARK and I'm not too sure what I should be doing.

The way I believe to go about this is as follows:

1. Shut down all programs needing IP connectivity, in order for those programs not to generate data, monitored by Wireshark.

2. Open Skype and establish a chat with a contact. Prepare a file like a pic or mp3 for uploading to that person.

3. Open terminal and type netstat DO NOT PRESS ENTER!!!!!

4. Open Wireshark and click on Pseudo-device that captures on all interfaces

5. Send the file you prepared to your Skype contact.

6. Once this file starts to send go to terminal and press enter.

7. Go to Wireshark and click on "List the available capture interfaces". 

8. When the file to your Skype contact has finished downloading go to Wireshark and click on "Stop the running live capture" 

Questions:
1. Will the netstat terminal command automatically stop after some time?

2. What is the best way to cross reference this data between terminal and Wireshark?

3. What exactly am I looking for now that I have the data?


Now that you know what I want to do I'm open to further suggestions and advice.

Thank you.

---

### Post by mikewhatever on 2011-02-05
I think all you need to do is run 'netstat -ptun | grep skype' when the file transfer is in process. You'll get the output related to skype with the remote IP showing. Then look up its geolocation.

---

### Post by suomalainen on 2011-02-05
@ mikewhatever,

Thanks for the input regarding <netstat -ptun | grep skype'>.

I did a Google search to learn more but it didn't turn up anything. I did try the command in terminal and the attached pic shows the message that appeared. So how do I get root then? What did I do wrong?

Thanks for your support!

---

### Post by mikewhatever on 2011-02-05
Nothing seems to be wrong. The two IP addresses are clearly shown. What else do you need? If you want to see all processes, run **sudo netstat -tupn**, but obviously, that might show many more then just Skype.

---

### Post by suomalainen on 2011-02-05
@mikewhatever,

This command wasn't run during a file transfer.

Also, what about the root complaint?

Thanks again

---

### Post by mikewhatever on 2011-02-05
Well, anyhow, Skype was connected to a remote computer, and its IP is in the output.
[http://whatismyipaddress.com/ip/88.112.195.44](http://whatismyipaddress.com/ip/88.112.195.44)
The root complain is not a complain, but rather a reminder, that if you want to see processes owned by root, netstat should be run as root. Skype is a user process, and is displayed when netstat is run with user privileges.

---

### Post by suomalainen on 2011-02-06
@ All,

Found this piece of information on line:

"Local time is shown according to server time. As server may be in different timezone, inadequate time may be shown sometimes.
Sorry, we cannot help this at the moment."

[http://www.shapeservices.com/en/support/forum/viewtopic.php?f=4&t=911](http://www.shapeservices.com/en/support/forum/viewtopic.php?f=4&t=911)

Regards. Suomalainen

---

