---
title: "X64 Skype non existant?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Rim on 2009-01-24
o.o ok i installed Ubuntu 8.10 AMD64 3 days ago and everything went great! It was a smooth install and i got everything i need in 2 hours even got compiz to work etc. But there is 1 problem i have with it.

^^ a 64 bit version of skype <.< is non existent or i just can't find it and can't talk to my friends.

o.o is there any other program that is similar and can conncet to other skype users or does a 64 bit version exist? If it does where and how do i install?

---

### Post by diablo75 on 2009-01-24
I believe there is a 64 bit version available via the medibuntu repositories.

Check this howto out:

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

Alternatively, (if you have 4 GB of RAM or less and the above doesn't work out) you might consider installing the 32-bit version of Ubuntu instead of the 64 bit version.  As far as I know, the only real advantage you get from using a 64-bit operating system is the ability to map more than 4GB of RAM.

Edit to add:

Here's [a thread]("http://ubuntuforums.org/showthread.php?t=432295") I tackled once where I put together some code for the terminal to install the medibuntu repositories and skype 64-bit in one shot.  You might try pasting this into the terminal:

```
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p bluez-alsa && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install -y --force-yes medibuntu-keyring && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install skype
```

---

### Post by Rim on 2009-01-24
:) hey thx a LOT! :D worked perfectly!:popcorn: O.O looks great, works fine! :)

---

### Post by diablo75 on 2009-01-24
> **Rim said:**
> :) hey thx a LOT! :D worked perfectly!:popcorn: O.O looks great, works fine! :)

Awesome!  Glad to know that worked.

---

### Post by ithanium on 2009-01-24
here is a link for the 64bit version:
[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

---

### Post by Victormd on 2009-01-24
The only thing is that your webcam won't work... :(

---

### Post by diablo75 on 2009-01-24
> **Victormd said:**
> The only thing is that your webcam won't work... :(

That depends...

---

### Post by ithanium on 2009-01-24
my built-in webcam works

---

### Post by braveerudite on 2009-05-03
> **ithanium said:**
> here is a link for the 64bit version:
[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

Dude thank you so much for giving away the link to Skype x64 for Ubuntu.  I was looking all over the official website for it.  I knew there was an official x64 Skype build but for some reason I didn't find it listed anywhere.  Would you please tell me how to find it for next time?  That way I keep checking for latest version

Thanks you again :)

---

