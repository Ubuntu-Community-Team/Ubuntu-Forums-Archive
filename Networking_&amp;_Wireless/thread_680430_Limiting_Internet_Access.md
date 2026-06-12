---
title: "Limiting Internet Access"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by TimMcE on 2008-01-27
I'm setting up a little limited user for myself, to use when I'm studying, to avoid the distractions inherent in trying to study on a computer with internet access.  I've created a desktop that only has shortcuts to the programs I need for study purposes, but unfortunately, one of these programs is Firefox, since several of my courses have online material.

What I'm wondering is if there is a simple way to limit Firefox to only those websites I need for studying, and block all the distractions like Youtube, Digg, Facebook, etc?  The caveat, of course, is that I only want to block those website from the one particular profile, while leaving my normal profile with full access to whatever I want.

---

### Post by ticopelp on 2008-01-28
You could edit your hosts file, of course, to block those sites you find the most enticing, but I think that would affect things across all profiles. 

```
sudo gedit /etc/hosts
```

You should see a line of code that says:

```
127.0.0.1	localhost
```

You can then add more domains to the file:
```
127.0.0.1	www.whatever.com
```

Restart Firefox and those sites will now be blocked. You can comment out the sites with # later if you want to gain access to them again.

I realize this is a little more low-tech than you might like, but it's worked for me in the past. Good luck.

---

### Post by TimMcE on 2008-01-29
Thanks, that might actually serve my purposes quite well.  Now, if there was some way of making two hosts files, and having a little script or some such that made say, restricted_hosts the active one when I logged into my study profile, and made unrestricted_hosts active when I logged into my normal profile.

But of course, I have absolutely no idea how to go about doing that.  Especially since editing hosts requires root, which I think means the script would have to store a sudo password, and storing root passwords in plain text doesn't seem to be the most wonderful of ideas.

But then, I could be wrong, since I really have no idea what I'm talking about.  But if anyone feels like correcting me, I wouldn't complain about that at all. ;)

---

### Post by firefeather on 2008-01-29
The Firefox extension [LeechBlock]("https://addons.mozilla.org/en-US/firefox/addon/4476") could be useful as well. You can set it to block those websites at a certain time of day or day of week or amount of time. Check it out.

---

### Post by arrrghhh on 2008-05-11
I use OpenDNS to block specific websites, and categorical filtering like "adult" websites.  Not sure that this would be a reasonable option for you, considering you want to be able to quickly switch between the two.  Perhaps two hosts file would be the best option (or that FF addon, which I've never used but looks like it's tailored to what you need!)

---

