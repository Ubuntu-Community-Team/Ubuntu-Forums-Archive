---
title: "How do I make my Ubuntu laptop secure?"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-10-12
I am very new to Ubuntu. I installed my first version with 10.04 and now I've upgraded to 10.10. I've actually only been using Ubuntu for about 4 days. 

I ABSOLUTELY love it. However, I'm a little confused about how to make it secure. A feature of Linux in general that attracted me was its stability and safety. 

I guess I'm wondering, is Ubuntu safe and secure out of the box? Are the default firewall settings "good enough?" Is Firefox the safest browser? Do I need anti-virus software? What is App Armor and how do I use it? Can Linux even get viruses? What about rootkits?

I understand that I have posed a lot of questions. I don't at all expect any one user to answer them all. Please just address one or two and let me know what you think.

Again, I'm VERY new to Ubuntu and computers in general. So, if you give me instructions, imagine you're talking to a 3 year old.

Thanks!

---

### Post by migs73 on 2010-10-12
AFAIK The firewall (UFW) is set to all ports closed by default.(doesn't get more secure than that!!)

Although viruses could (can) be written for Linux, there are no known ones 'in the wild'. Even if one did infect your PC the compartmentalised set up of Linux means the chances of it destroying everything is very remote.

look here for more info from someone who know an awful lot more than me;
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by celticbhoy on 2010-10-12
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Hippytaff on 2010-10-12
I've never had any problems out of the box as far as security goes, I know some people tweak the firewall etc

---

### Post by cwbar_1 on 2010-10-12
Greetings!  You don't have to worry about security for your new Ubuntu installation.  Completely safe out of the box. Been using Ubuntu for 4 years without additional protection.  Nothing has ever happened.  99.999% of all viruses cannot execute in the linux environment.  
If you are using a wireless router,  use the normal security settings for any network.

---

### Post by oldsoundguy on 2010-10-12
The best way is to modify the component sitting in the chair.
A change in attitude is the first step.  Realizing that Linux is not Windows.
Set your passwords at REAL passwords .. not something from the dictionary. (breaking up a multi syllable word with numbers is the easiest .. that way it can be remembered!)
Stay away from non repository sources for your software .. exceptions are those sites and PPA's with a known GOOD reputation.
ALWAYS check your software center or Synaptic for the version of the program FIRST before you go out of repository to install.  It may not be the latest version, but it will WORK on your set-up most of the time. Bleeding edge versions are really not what they are cracked up to be in most cases.
(but remember that installing is not like a Windows install that puts stuff in the registry and all over.  IF you need to remove a program .. it is simply removed with no major clean up required. (Such as removing McAffee or Norton from a Windows machine!!))
Ask HERE about 3rd party programs before you install.  Some should be installed with a users manual and it is NOT there (Ubuntu Tweak comes to mind .. good program, but takes some time to find out what it actually does and what to avoid doing out of the box).. so ASK!

---

### Post by AndyM3 on 2010-10-12
You don't need to **make** it secure. Ubuntu **is** secure already.

The default firewall settings are to block everything, which is as secure as firewalls get.
Firefox is safe enough for normal use anyway, but you may want to install WOT (Web of Trust), FlashBlock, BetterPrivacy, Beef TACO and other security/privacy extensions. If you're really paranoid, install the NoScript extension (which blocks all JavaScript, Flash, Java etc. content) or just use lynx, the safest browser on earth. :P
You probably don't need anti-virus software unless you're running a mail server.
AppArmor is an anti-malicious-applications system, kind of like SELinux but you don't have to manage it and you don't get thousands of alerts per day. It's active by default AFAIK.
Linux can theoretically get viruses, but it's really, really rare. As for rootkits, I don't really have any knowledge of them, but I know there are some applications that remove rootkits (rkhunter comes to mind).

But yes, have a strong password. To see what "strong" means, look up "diceware".

---

### Post by cariboo on 2010-10-12
For more info on securing your laptop, have a look at the stickies in the [Security Discussion]("http://ubuntuforums.org/forumdisplay.php?f=338") sub-forum.

---

### Post by Megaptera on 2010-10-12
Another good p/w generator:

[http://www.passwordcard.org/en](http://www.passwordcard.org/en)

---

### Post by Ranger_Joe on 2010-10-18
Guys, I read something this week about how Linux doesn't give users administrator level access by default. It only runs in this mode SOME of the time. I guess that's another way that it stays secure, by not allowing attacks to have administrator level access through you. 

Can someone tell me more about this? When should I be using my administrator privileges? How do I know when this is "turned on?"

---

### Post by Ranger_Joe on 2010-10-18
BTW, AndyM3, your wallpaper is sweet. Where did you get it? Is that a sneak peak at 11.04??

---

### Post by arpanaut on 2010-10-19
> Can someone tell me more about this? When should I be using my administrator privileges? How do I know when this is "turned on?"

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This will give you a good basis for understanding that aspect of running Ubuntu

---

### Post by 3rdalbum on 2010-10-19
Correction: The firewall does not "block everything by default". It let's everything in by default. This is not actually a problem, because by default there is nothing listening for connections anyway.

---

