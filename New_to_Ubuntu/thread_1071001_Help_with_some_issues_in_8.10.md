---
title: "Help with some issues in 8.10"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by xonecas on 2009-02-15
Hello, this is my first post since I finally switch Ubuntu as my main OS, yeah I'm  still run xp in virtualbox but it was to support my ipod, but it does not work.  I am really happy with my new system.  I had attempted the transfer to linux several times before but to many problems out of the box, that it scared me off.  Not with Ubuntu 8.10, runs smooth, desktop effects, conky, wireless works as soon as I enabled the restricted driver. I'm in wonderland, building websites with free tools, learning about bash and scratching the surface of programing languages.

Here is a list of problems i could use some help with.
I did some searching around in the forums but i was unable to find existing solutions for my problems.

1. My latest gen (4th) ipod nano does not play well with linux.  I tried native solutions like rythmbox/banshee/gtkpod/amarok with no good results.  My next attemp was using my virtual XP machine to run itunes, everything works good right until i try to start itunes.  The service starts in the background, the itunes window never shows making it useless.
i tried wine + itunes, no solution, its buggy, unreliable, and it does not support my ipod.  I think i found my solution with songbird but haven't tested it yet.  Any ideas if songbird does not work? (i will post the result of that in this post).

2. I followed guides and howtos to perform the wine compilation with the msi patch and now i cant remove wine from my system, which i would really like to. Its not listed as installed in my synaptic package manager.  I also installed songbird from a tar-ball and just after i found a deb package. Using the tar-ball i don't know where to place the songbird folder, and the install just looks messy. My question is how to remove my existing songbird so that i can use the deb installation file; and how to get rid of my "custom" wine installation.

3. General system maintenance. From using windows for such a long time, got me paranoid about having no "clutter" files in my system, making sure i remove and clean any unwanted files or folders, performing correct installations and removals. I am looking for some guide or directions on how to ensure that my ubutu systems stays lean and fast with only the necessary software installed for my needs.

Thank you for you time, and any help will be greatly appreciated !
Sean

---

### Post by photonian on 2009-02-15
for #2 --  There should be an uninstall script in the folder you installed it from

for #3 --  You might look at Menu-System-Preferences-Sessions and Menu-System-Administration-Services
            and "apt-get install bum" - a Boot-Manager GUI

---

