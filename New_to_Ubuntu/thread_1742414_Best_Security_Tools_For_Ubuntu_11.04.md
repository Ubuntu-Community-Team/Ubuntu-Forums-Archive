---
title: "Best Security Tools For Ubuntu 11.04?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Riku Reed on 2011-04-28
Does anyone know of a good resource for security tools I can use for my system to block out any potential threats if one where to come, like an anti-virus tool, something so to say to block anything that could be tracking my usage on the internet, I know Firefox 4 can browse in a private mode, are there any browsers that allow me to be completely anonymous?
Hm, well for anti-virus, If I were to download a virus by mistake such as a trojan horse or rootkit that isn't easily detectable thats written for Windows, by chance is it possible for that file to somehow get into my system? Such as downloading it in a administrator account? By means of root, I'm usually always on one account on my PC and I'm not to sure between the difference of a account having admin. rights and that of a root account? And out of curiosity say I download a rootkit, keylogger, anything of high threat and I have Wine installed on my account (Which is only one account I created after a fresh install) could that virus get into wine?
Other than anti-virus, does the default firewall keep other users out of my system? The one that typically comes installed after a fresh install from a CD/USB. Say can that firewall keep hackers from getting access to my computer?  Such if one were to obtain access, I'd hate to be spied on through my webcam by some creep. Can the basic firewall be cracked? If so could they watch my screen? Or do other things say mess around with my system settings, possibly deleting important files?

If so to having the possibility of any of that happening, how in a way of saying should I handle it if it were to happen. Are their any tools to use to keep *that* out.

---

### Post by K_45 on 2011-04-28
Install Ghostery in Firefox 4 + Noscript. The root account is disabled by default in Ubuntu. I don't think any current malware in the wild affects Linux. You don't need antivirus unless you share files with Windows, and even then its optional. I'd configure ufw and leave it at that:

```
sudo ufw default deny
```

```
sudo ufw enable
```

---

### Post by deconstrained on 2011-04-28
Install/configure AppArmor to begin with. That will reduce the chances of weaknesses in software you have being exploited. But before even that, check the services you have running on your machine, disable ANY that you don't need, make sure they are all running as "nobody" or with some other unprivileged UID/GID, etc., and in general just make sure that gaining root access to your machine remotely is not possible; to do otherwise would just be bending over.

Install SELinux if you want to be more hardcore...

As for tracking of your internet usage: sign up for a VPN, or use Tor if you don't feel like paying a monthly service fee at the expense of slower internet. Your ISP can pretty much see everything you do.

---

### Post by 3rdalbum on 2011-04-28
1. If you want to be fairly well anonymous, try using Tor.

2. No, computer viruses written for Windows will not just "spontaneously execute themselves" on Linux. Not even if you have Wine installed. The only chance of this would be if you downloaded them in a web browser or e-mail client running in Wine; and even then, probably wouldn't happen. You shouldn't be using a web browser or e-mail client in Wine anyway. And there's no viruses on Linux.

3. A firewall stops remote computers from connecting to your computer, so basically yes it will stop attackers from connecting. You don't actually need a firewall on Ubuntu anyway, really; a default installation of Ubuntu doesn't listen for any incoming connections anyway. You'd just need a firewall if you install any services that listen for incoming connections from remote computers.

The most important security tools for you to use are:

a. Update Manager, to patch any known security vulnerabilities when they are discovered
b. Your brain, to stop you from downloading and running anything that looks suspicious.

Ubuntu is fairly secure out-of-the-box. Keep it up-to-date and you really won't need to worry about security.

---

### Post by Riku Reed on 2011-04-28
About SELinux, on Wikipedia, I looked it up and read through on it. Don't seem to know how it's to be installed after so it says its a feature, the page shows SELinux on Fedora 8. Is it the same with Ubuntu, a way to install it?

About Tor, I installed it, did it quickly through terminal. "sudo apt-get install tor". It said its installed, I'm not to sure how it works, is it neccessary to configure it or should I leave it be?

---

### Post by K_45 on 2011-04-28
You'll need to configure Tor, but I wouldn't use it unless you really need it, its too slow for general browsing.

---

### Post by Riku Reed on 2011-04-28
Well much appreciated, most of my questions got answered thanks :D

---

### Post by oldos2er on 2011-04-29
Also read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by felixq78 on 2011-06-09
It appears that 11.04 has a firewall installed by default, I only discovered this when Frostwire detected it and it appears that the firewall prevents Frostwire from running at full speed. Can't get a "Turbo" connection just what they call a "Good connection". I'll be un-installing it asap.
Why would they think that we need a firewall on Ubuntu 11.04 when we've been using it for years without the need for one. I've kept with Ubuntu since 7.04 and have never needed one.
Has something changed that we now need a firewall ?

---

### Post by oldos2er on 2011-06-09
iptables is installed by default on most if not all Linux distros, if I'm not mistaken. In Ubuntu it is installed but not activated because there are no services listening on any ports. If you're behind a router, that's probably what Frostwire's detecting.

---

### Post by Paqman on 2011-06-09
> **oldos2er said:**
> If you're behind a router, that's probably what Frostwire's detecting.

Indeed, you might need to forward some ports. Check Frostwire's documentation.

---

