---
title: "Non root user permissions"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2010-11-09
Hey

Does anyone know of a solution by bypasses the user having to do
sudo halt

I'm running Back|Track 4 R1, but I never use root but I have got
audio to work :D by adding my user to the audiio group

Also, about kpowersave, the options like 
Suspend to Disk
Suspend to RAM
Set CPU Frequency Policy
are all greyed out

Cheers

---

### Post by CharlesA on 2010-11-09
BT4 is meant to be run as root. I'd suggest posting over on the backtrack forums to see if they have any ideas.

---

### Post by Pevichaey5 on 2010-11-09
BackTrack forums are scary lol

I've only posted once or twice, and got a warning for it, never
went back again

Thanks though

---

### Post by CharlesA on 2010-11-09
You using it as yer desktop OS then?

---

### Post by Pevichaey5 on 2010-11-09
I normally try to use the CLI as much as possible so that it 
hopefully consumes as little power as possible (its an Eee PC)

It is the only OS on here, basically, I have a Win7 desktop for
gaming and music, NetBook for everything else, that was including
the BackTrack WiFu course as well

---

### Post by CharlesA on 2010-11-09
Gotcha. If it's for Wifu, I'm not sure what all would be needed to be done.

That being said - I haven't really run into any real power problems when running backtrack 4 on my eeePC, but then I just run it as root since that's all it's used for.

---

### Post by Pevichaey5 on 2010-11-09
Yea, well after passing the BackTrack WiFu, it basically became
my primary OS, as I needed to use tools etc and for a while any
debian based OS would have been fine, but it just seemed a real
hassle having to install the tools I wanted to use, so I just 
stuck with BackTrack

---

### Post by CharlesA on 2010-11-09
I'm not sure how yer user is set up, but can't you just install sudo and add yerself to the sudoers file?

I've never used it as a primary OS, it's always been virtualized for me (hurray for USB wireless cards)

---

### Post by Pevichaey5 on 2010-11-09
Sorry, but I have already done that part

I can shut it down, its just a nusence that I have to
sudo halt
password
etc, but with things like kpowersave, I'm not sure how to start
those up using sudo :(

I have to start wicd which is no problem
sudo /etc/init.d/wicd start
wicd-cli -y -S
wicd-cli -y -l
wicd-cli -y -c -n x

So in terms of networking I'm sorted, I'm just really after 
removing the need for sudo on halt and I assume my kpowersave 
problem is because I didn't sudo

---

### Post by CharlesA on 2010-11-09
Yeah.. it gets complicated since the distro was meant to be run by root, not an unprivlaged user.

Best bet would be to either search their forums, or ask there.

---

### Post by Pevichaey5 on 2010-11-09
Cheers for the help 

Much apprechiated :D

---

