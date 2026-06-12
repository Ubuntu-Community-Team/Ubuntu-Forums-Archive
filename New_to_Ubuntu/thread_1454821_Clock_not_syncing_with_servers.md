---
title: "Clock not syncing with servers"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by pj_kare on 2010-04-15
My systems time is mostly wrong even though it's set to sync with time servers. Using System-Administration-Time and Date does not allow any changes to time, any manual changes quickly revert back to what they were. The only way I can set time is by right clicking on the Clock and selecting preferences and setting time that way. (Or is that normal).
After quite a few attempts using manual SYNC I finally get a Syncing with Server message and then get this error:
```
The configuration could not be saved:
Invalid data was found.
```Server and location are all set properly, and if I change the time (via the clock applet) to something ridiculous, and try to sync manually or select Automatically update from server, nothing happens, though I do see information being sent/received on the internet connection indicator.
Any thoughts? Thanks.

---

### Post by r-senior on 2010-04-15
Could you try a couple of things in a terminal?

$ sudo ntpdate ntp.ubuntu.com

Post the output unless it reports that the NTP socket is in use. If the NTP socket is in use:

$ sudo /etc/init.d/ntp stop
$ sudo ntpdate ntp.ubuntu.com

and post the output from the second command. If you had to stop NTP, restart it again like this:

$ sudo /etc/init.d/ntp start

---

### Post by pj_kare on 2010-04-15
Thankyou for the reply, it is most appreciated, this is the output.

```
****@****-desktop:~$ sudo ntpdate ntp.ubuntu.com
16 Apr 08:18:36 ntpdate[1931]: adjust time server 91.189.94.4 offset -0.055085 sec
****@****-desktop:~$ sudo /etc/init.d/ntp stop
 * Stopping NTP server ntpd                                              [ OK ] 
****@****-desktop:~$ sudo ntpdate ntp.ubuntu.com
16 Apr 08:18:57 ntpdate[1951]: adjust time server 91.189.94.4 offset -0.048042 sec
****@****-desktop:~$ sudo /etc/init.d/ntp start
 * Starting NTP server ntpd                                              [ OK ] 
****@****-desktop:~$
```I get the "Syncing with server" message when trying manually mostly when I have a webpage either reloading or opening, any other time it hardly ever appears, either way it doesn't work. 

EDIT: I just set the clock to the *wrong* time via the clock preferences, (changed it by around 10mins). Tried to sync both manually and using automatic and nothing happened, I then tried the code you gave  "sudo ntpdate ntp.ubuntu.com" and I watched the time change to about what it should be, I assume it's the correct time.  I also tried adding "ntp.ubuntu.com" to the server list and it didn't help.

I at least now know that I can sync time through Terminal. Thanks for that.

---

### Post by pj_kare on 2010-04-16
**For anyone that's interested**....after doing a lot of searching for a solution, I found this web page:
[https://help.ubuntu.com/community/UbuntuTime#Can%20these%20servers%20be%20resolved?]("https://help.ubuntu.com/community/UbuntuTime#Can%20these%20servers%20be%20resolved?")

It mentions this:

> **Can these servers be reached?**

 If ntptrace $servername etc etc etc.............So I thought I'd try that command (ntptrace $servername) in a Terminal, using the Australian NTP servers listed in Time And Date Settings and this is what I got.

```
****@****-desktop:~$ ntptrace time.esec.com.au
time.esec.com.au: timed out, nothing received

****@****-desktop:~$ ntptrace ntp.per.csiro.au
No address associated with hostname

****@****-desktop:~$ ntptrace ntp.adelaide.edu.au
ntp.adelaide.edu.au: stratum 2, offset -0.003033, synch distance 0.205549
ntp1.nl.uu.net: stratum 1, offset 0.000000, synch distance 0.000483, refid 'PPS'

****@****-desktop:~$ ntptrace **ntp.cs.mu.oz.au**
ntp.cs.mu.oz.au: stratum 2, offset -0.000302, synch distance 0.200023
***Association ID 584 unknown to server

****@****-desktop:~$ ntptrace ntp.mel.nml.csiro.au
No address associated with hostname

****@****-desktop:~$ ntptrace ntp.nml.csiro.au
No address associated with hostname

****@****-desktop:~$ ntptrace ntp.per.csiro.au
No address associated with hostname
```Only 2 of the time servers actually responded, it seems as though the others no longer exist, so I set **ntp.cs.mu.oz.au** as the time server, and it actually automatically synchronised a couple of times. (I purposely set the time **wrong** to test it.) The only thing is that you have to wait a while for it to update, it doesn't happen straight away.
Which is probably why it didn't change in my previous attempts at using different servers. Selecting **Manual** and clicking the **sync** button still does nothing!

**Update before posting:** Changed time again to "wrong time" to run test again and it hasn't work after over 2 hours (not sure how often time is suppose to sync). Added the other seemingly working server (**ntp.adelaide.edu.au**) and waiting once again........hurrah it has finally worked. I'm thinking the other server is not always available, probably because of my crappy dialup connection.
AND....**Manual** **sync** still does nothing!!!
Hope this information is of some use to someone someday.:confused:

---

