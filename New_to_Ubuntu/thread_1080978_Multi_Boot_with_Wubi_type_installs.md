---
title: "Multi Boot with Wubi type installs ?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by music_1 on 2009-02-26
Not sure if I'm just using the wrong type of search for existing threads, but I couldn't find my answer.

I have installed a Wubi version of Ubuntu 8.10 on my XP machine. I have just realised that Mint has a somewhat similar "install inside windows" available on the install CD. I chose to install hoping for a tri-boot grub type option. Wrong!

This now means that when booting up that only XP and Mint are available to boot to - and I'm at a loss in recovering my Ubuntu install.

I know that having two Linux versions inside XP is probably frowned upon and best left to GRUB to manage from installing properly. Presumably there are people out there choosing, or at least wanting, to look at the Ubuntu family of distros at the same time without wanting to commit to full installs.

In short, how do I recover the boot to Ubuntu option (inside Windows) and can I have Ubuntu, Kubuntu, Xubuntu and Mint all available from the boot to options?

---

### Post by stoogiebuncho on 2009-03-01
Generally when you install Ubuntu via WUBI, it does not install GRUB.  The startup options are actually handled by Windows.

I believe you can view the options by going to 
control panel > system > advanced > startup and recovery

You could also try looking in your c:\boot.ini file.

I can't tell you exactly what you'll need to change, but it you look at what it says for your Mint option, you might be able to figure out what you need to add for the Ubuntu Option.

---

