---
title: "Internet cut off after having installed Firesterter"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by cromulent on 2007-03-11
Hello. I really don't know much about Linux, but I'm working at it. 
I have a T30 thinkpad with Xubuntu 6.10 and a Belkin pcmcia card. 
I rescently installed firestarter and since then I haven't been able to access the internet. So, here is what I did. 

1) I uninstalled firestarter and the problem didn't go away

2) I checked the forums (what I should have done first) and saw that firestarter modifies the same files that iptables modifies so I should look at that. 
I typed iptables -L into the terminal but it had no special rules. Everything was set on ALLOW

3) I then checked for scripts firestarter may have left in /etc/init.d .  There was a script called "firestarter" so I moved it. 

4) I have restarted using the life cd and the internet works, so I'm confident that this isn't a hardware problem. 

5) I've run out of ideas, so here's hoping that you guys can help. 

Thanks in advance

---

