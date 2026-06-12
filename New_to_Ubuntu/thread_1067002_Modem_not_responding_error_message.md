---
title: "Modem not responding error message"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-02-11
Hi,

I'm trying to sort out an old PC given to an elderly friend.  Following advice elsewhere in the Forums, I've installed Xubuntu, which I've never used myself.  (I'm pretty new to Ubuntu.)

I've followed the online help for advice on configuring the modem, and setting up a dialer: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9).  Using wvdial, I got as far as getting a connection, but it kept disconnecting almost immediately.  Still following the instructions, I used ```
gksudo gedit /etc/ppp/options
``` to comment out lcp-echo-interval30 and lcp-echo-failure4. At this point, I seem to be connected, but Firefox and Thunderbird are unable to connect.  

The instructions say > If you connect successfully but your Internet applications do not function (eg. web pages do not load in Firefox), you might need to add replacedefaultroute as a new line in the pppd option file.   I assumed I should do this using the above code, and added the line at the end of the file.  However, when I then tried ```
sudo wvdial
``` the process started but then gave an error message of "modem not responding".  I went back and removed the line from the end of the file, but still get the error message.  Please can somebody tell me where I'm going wrong?

Thanks.

Lesley

---

### Post by LowSky on 2009-02-11
sudo wvdial would try to open that program using root access, which is wrong, and why it failed.

You need to edit the file of /etc/ppp/options using this command:
```
gksudo gedit /etc/ppp/options
```

at the end of the document you just opened copy and past this on its very own line
```
replacedefaultroute
```

then reboot the PC and try dial up agian

---

### Post by Bearly Able on 2009-02-11
Hi LowSky,

Thanks for the help. ```
sudo wvdial
``` is the code given in the help files, so if this is wrong, other folk will run unto the same trouble.
> You need to edit the file of /etc/ppp/options using this command:
Code:

gksudo gedit /etc/ppp/options

at the end of the document you just opened copy and past this on its very own line
Code:

replacedefaultroute



That's exactly what I had done when I first ran into the "modem not responding" error.  I'll try it again, then run wvdial without sudo and see what happens.  I'm at home just now, so I'll have to wait till the morning to try this.

Lesley

---

### Post by lkraemer on 2009-02-12
Why not start out by trying Alternative Way 1 (using wvdialconf & wvdial)
first.  If you have wvdial's configuration correct it should dial, connect,
and transfer the connection to ppp.

Then when you have it working you can progress on to other methods.

Note: In your wvdial terminal window, you must leave it open,
while the connection is in progress.  Only close it when you are 
finished with the connection.  I just minimize mine.  

When you're satisfied it all is up to snuff, try gnome-ppp, or another
choice.

lkraemer

---

### Post by Radioman991 on 2009-02-12
My 0.02

In the OP, you stated this is an old PC.  In my experience, with my father-in-law, the Dell I set up for him had an old Winmodem in it.  Functionality was hit and miss.  It would work 2 times, and never work again.  I fought and fought with it.

Finally went to Staples, and bought an external US Robotics serial modem.  All my dial-up problems, and trips to Jack's house all but ended.

YMMV

Radioman991

---

### Post by Bearly Able on 2009-02-12
Hi Guys,

Thanks for taking the trouble to reply.  I think I wasn't clear in my original post.  I have been trying Alternative Way 1, and seemed to have the configuration finally figured out.  I've tried again today following LowSky's suggestions and that's solved my original error message, but I still can't get online.

When I use wvdial, it apparently dials and connects OK, and I eventually reach a line saying "Using interface ppp0".  (Before I get there, I get warnings that PAP and CHAP may be flaky, which I don't understand.)  I assume at this stage the modem's connected, but I still can't get Firefox or Thunderbird online.  I've triple-checked that I followed the instructions
> at the end of the document you just opened copy and past this on its very own line
```
replacedefaultroute
```
then reboot the PC and try dial up agianbut still the same problem.

I also keep getting ```
The PPP daemon has died.  A modem hung up the phone (exit code 16)
``` even though I've already commented out lcp-echo-interval30 and lcp-echo-failure4.

I've just been given a second-hand Mercury serial modem.  (It doesn't have a model number on it.)  I can try configuring it the same way, but if I run into the same problems, I still won't know what to do to solve them.  I understand that buying a new modem may be the easiest solution, but I can't easily do so, as there are no computer shops on the island, and most suppliers have a £20+ carriage surcharge to the Highlands and Islands.

Any further help would be most appreciated.

Lesley

---

