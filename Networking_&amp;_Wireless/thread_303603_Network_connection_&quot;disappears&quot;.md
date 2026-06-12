---
title: "Network connection &quot;disappears&quot;"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by greew on 2006-11-20
Hi,

I just reinstalled Kubuntu on my laptop. Now it seems, that sometimes when I use firefox, the connection of the my computer suddenly disappears.

I'm using wireless with WPA. I still have an IP address when the problem arises, but I'm not able to ping anything - not even my router. 

I haven't seen a specific interval for this, but I would say that the problem happens between every half hour and two hours.

I don't know if it's true, but it seems that the problem arises when I use firefox after not having used it for some time - I'm not sure about this - firefox might just have been the first thing I'm using after the problem comes.

Does anyone has an idea of what's wrong or where I can search for more information?

Best regards,
Jesper

---

### Post by greew on 2006-11-20
And believe it or not - it happened while I wrote the post above - GRRRRRR!!!!

---

### Post by stream303 on 2006-11-21
Sorry - that was me, I've got a non-functioning light switch in the room and...  (ok bad attempt at humor) :)

Have you tried disabling IPV6 in Firefox?
1) In the url bar, type about:config
2) seach for IPV6 in the filter
3) toggle the boolean state (doubleclick the filter result on the left) to true to disable
4) restart firefox

You may want to try a global disabling of IPV6 if that works:
edit (as root, ie sudo gedit)
1) create a file titled **bad_list**
2) in /etc/modprobe.d directory
3) bad_list should contain only one line: **alias net-pf-10 off**
4) reboot or restart networking.

Let's see if this helps...

---

### Post by greew on 2006-11-21
Ok.. I've tried both now - so I'll let you know how it goes!

---

### Post by greew on 2006-11-22
Ok - until now I haven't had any problems with my connection anymore

Stream303: thank you so much for your help! It was great!

Best regards,
- Jesper

---

### Post by Etlaesium on 2006-11-22
I am having the same symptom, but from a different cause (IPv6 is already disabled).  Any thoughts?

---

### Post by stream303 on 2006-11-23
Hmm..  how's your dns?  If you are running a router and dhcp, you may want to take a look at this:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

