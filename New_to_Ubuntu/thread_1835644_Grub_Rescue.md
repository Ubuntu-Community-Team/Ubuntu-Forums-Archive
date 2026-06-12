---
title: "Grub Rescue"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by Mashai on 2011-08-29
Sorry if this is somewhere else. I looked, but all the other grub rescue questions seemed to be about much more complex things written by people who know a whole lot more than me.
 
Anyway...
 
So, I did a clean install of the latest version of Ubuntu from the website from a USB drive. I did this on a brand new hard drive with absolutely nothing else on it.
 
It seemed to install perfectly, except when it restarted after the install, it took me to 'grub rescue' (and continues to do so).
 
...The hell is this? I just want to use Ubuntu. What do I do?
 
It might help to note that I'm on a laptop.
 
EDITED: For spelling and grammar.

---

### Post by gnometorule on 2011-08-29
What laptop are you using? I'm dual booting on a Toshiba netbook. While it's not documented in any official source I know of, I need to adjust options in the boot menu to boot either into Ubuntu 10.04, or into W7: one boots only with a particular option selected, the other only with the other option. It's probably some bug, but not worth breaking sweat over once you know. I'd need to restart to remind myself of the precise name of the option (in the advanced sub menu for me), but it's I believe SATA 'compatility mode' vs another...so if it's a Toshiba, restart, hit F2, adjust to whatever it currently is not, and you might be able to get into Ubuntu w/o a problem. Next time you use W7, simply undo the selection, etc etc.

Edit: the behavior you describe is exactly what I'm experiencing.

---

### Post by Rex Bouwense on 2011-08-29
Everything that you ever wanted to know about Grub2 including how to solve the problem that you are having can be found at this web site:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

By the way welcome to the forums and remember that a Google search is your friend.:popcorn:

---

### Post by Mashai on 2011-08-29
> **Rex Bouwense said:**
> Everything that you ever wanted to know about Grub2 including how to solve the problem that you are having can be found at this web site:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")

By the way welcome to the forums and remember that a Google search is your friend.:popcorn:
Understanding what this website has to tell me requires a level of competence I've yet to reach. I've been there. They told me something in a language foreign to me. I came here next.

---

### Post by raja.genupula on 2011-08-30
> **Mashai said:**
> Sorry if this is somewhere else. I looked, but all the other grub rescue questions seemed to be about much more complex things written by people who know a whole lot more than me.
 
Anyway...
 
So, I did a clean install of the latest version of Ubuntu from the website from a USB drive. I did this on a brand new hard drive with absolutely nothing else on it.
 
It seemed to install perfectly, except when it restarted after the install, it took me to 'grub rescue' (and continues to do so).
 
...The hell is this? I just want to use Ubuntu. What do I do?
 
It might help to note that I'm on a laptop.
 
EDITED: For spelling and grammar.


goto your Bois settings and set to  boot from your external hard drive . let us know what you got

---

