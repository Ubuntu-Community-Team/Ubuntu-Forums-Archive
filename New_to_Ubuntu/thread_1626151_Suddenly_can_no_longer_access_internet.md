---
title: "Suddenly can no longer access internet"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Emilyann on 2010-11-19
Hello dear all :)
I have been happily using Ubuntu for about a month now after alot of help from the forum members setting it up.
But Im having problems again and I need to ask for more help please!
I am using a wireless broadband internet connection. It was working fine on the Ubuntu computer- but mysteriously now the computer doesnt seem to be able to connect to the net. I cant think that there have been any settings altered or softwares installed that could be the culprits- but Im really clueless so Im willing to try anything!
I know the broadband plug in dongle thing is working fine as Im sitting here next to the PC on a spare laptop and am able to connect and access the web with no problems.
When I click on the connection icon at the top of my Ubuntu screen I have a drop down menu offerring Enable Neworking ( which has a tick next to it)
Enable Notification ( also ticked)
Connection Information
Edit Connection
About
 
When I go to edit connection, my usual 3G stuff is all there, and Connect automatically is still checked- as it always was.
When I pull up the other menu offering me to select my 3g connection- the little icon makes moves as though it is scanning for the connection- but then quickly says it cannot find a connection or some other such thing that indicates its not finding whatever it needs to go online
Ive got the wireless dongle thing plugged into this laptop so Im having to swap and change between them between each step so apologies for my delays caused by this!
Many thanks for any assistance anyone can give!

---

### Post by waynefoutz on 2010-11-19
open a terminal and type 

```
lsusb
```

and see if the broadband modem is listed in the results.

If it's listed in NetworkManager's pull down menu it probably is. If so, sometimes I've found that going into "edit connections" and deleting the mobile broadband connection, then setting it back up like you did the first time you did in Ubuntu usually does the trick.

---

### Post by Emilyann on 2010-11-19
ok so when I do that with the USB thing plugged in I get a result line showing:
ONDA Communication S.p.A ZTE MF 636
amongst all the rest of the sode lines, but when I pull the usb thingo out to put it back into this laptop this line is gone- so Im assuming this is the broadband mobile device.
I will go through and set it up again and see if this fixes it up, thanks for the suggestion!
Back to let you know how it goes shortly...

---

### Post by Emilyann on 2010-11-20
Deleted and then reinstalled with correct details etc as was suggested and the problem persists unchanged sadly :(
 
Also did this again but with a restart to the computer for good measure- also no luck.
 
bit stuck on what to do from here!

---

### Post by Emilyann on 2010-11-20
does Ubuntu have something similar to microsofts  System Resore? Grasping at straws- but I thought since this was all working fine 3 days ago, maybe I could reset everything back to it was then?

---

### Post by cressrt on 2010-11-20
I have to use a Mobile dongle as that's the only way we can connect to the Internet. We use Vodafone and used Betavine to connect when running 9.10 and also had success with Stakis. Since upgrading to 10.10 we have had no problems connecting, the built in software finds and connects without any problems.
So what version are you running? I found lots of help available by searching this forum which enabled me to originally set up a connection. As you can see I'm a newbie as well but like trying to help.

---

### Post by Emilyann on 2010-11-20
thanks so much cressrt for replying....I am also using 10.10 and for many weeks it had been connecting beautifully! I dont really know what to do now :(

---

### Post by dineshs on 2010-11-20
See this guide
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)   
what do you get for
```
dmesg | grep -e "modem" -e "tty" 
```?

---

### Post by cressrt on 2010-11-20
It may be worth trying the SIM card in a mobile to make sure it still works OK or if have another SIM try that in the dongle.  Our dongle often asks for the PIN code, but not always when it is unplugged and plugged n again.  Sorry cannot be of more help.

---

