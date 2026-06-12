---
title: "[SOLVED] black !!!!! peach!!! arrggghhh!!"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by nubix on 2008-12-29
hello ubuntuforums.org i have a problem that im sure is easily fixable by you seasoned Linux enthusiasts.

i have an old dell dimension 2400 that i just upgraded from 256 memory to 512 from all the scrapped comps i just got hold of. i figured id fix it up and make it into a family internet browsing computer. only problem is after installation i start it up log in, i hear the rain forest startup sound, bam screen goes black, with only my cursor showing. so for some reason i go into change session and select gnome for just one session on the second startup and instead after log in, i get no rainforest drum sounds, but the peach backround is still there. i have tried to restart it many times tried it once in failsafe gnome even.... i just have been getting the same peach screen.

please help! i have installed and used Linux flawlessly on many other machines. sorry for the mangled english, it was kind of a cursory post. :)

---

### Post by LowSky on 2008-12-29
sounds like your Xorg file is messed up, boot into recovery mode form grub and choose xfix

---

### Post by nubix on 2008-12-29
ok i did that it rewrote everything, it was done i hard reset my box, and it was the same familiar peachy soundless screen after login.

---

### Post by oldos2er on 2008-12-29
What video card do you have?

---

### Post by nubix on 2008-12-29
mobo built in

---

### Post by nubix on 2008-12-29
hello ubuntuforums.org i have a problem that im sure is easily fixable by you seasoned Linux enthusiasts.

i have an old dell dimension 2400 that i just upgraded from 256 memory to 512 from all the scrapped comps i just got hold of. i figured id fix it up and make it into a family internet browsing computer. only problem is after installation i start it up log in, i hear the rain forest startup sound, bam screen goes black, with only my cursor showing. so for some reason i go into change session and select gnome for just one session on the second startup and instead after log in, i get no rainforest drum sounds, but the peach backround is still there. i have tried to restart it many times tried it once in failsafe gnome even.... i just have been getting the same peach screen.

please help! i have installed and used Linux flawlessly on many other machines. sorry for the mangled english, it was kind of a cursory post.  :) thank you in advance.

---

### Post by abn91c on 2008-12-29
> **nubix said:**
> hello ubuntuforums.org i have a problem that im sure is easily fixable by you seasoned Linux enthusiasts.

i have an old dell dimension 2400 that i just upgraded from 256 memory to 512 from all the scrapped comps i just got hold of. i figured id fix it up and make it into a family internet browsing computer. only problem is after installation i start it up log in, i hear the rain forest startup sound, bam screen goes black, with only my cursor showing. so for some reason i go into change session and select gnome for just one session on the second startup and instead after log in, i get no rainforest drum sounds, but the peach backround is still there. i have tried to restart it many times tried it once in failsafe gnome even.... i just have been getting the same peach screen.

please help! i have installed and used Linux flawlessly on many other machines. sorry for the mangled english, it was kind of a cursory post.  :) thank you in advance.
ctrl+alt+f1, then at the prompt type 
[COLOR="Blue"]**sudo apt-get remove compiz**[/COLOR], followed by[COLOR="blue"] sudo apt-get remove compiz-core[/COLOR], then reboot and enjoy ubuntu.

---

### Post by nubix on 2008-12-29
there is not promt that comes up......

---

### Post by abn91c on 2008-12-29
did you press the ctr alt f1 keys?

---

### Post by nubix on 2008-12-29
yes, at startup after log in i pressed those keys... nothing......

---

### Post by abn91c on 2008-12-29
reboot when you see the prompt "press ESC for menu options" or something similar,  do that, then select the recovery kernel, after ubuntu loads, there will be a few choices, try the xfix option first, if that dont work select the prompt choice then do the commands to remove compiz

---

### Post by nubix on 2008-12-29
well that worked! gratz to you! pat yourself on the back my friend!! :P i am kind of disapointed that i cant run compiz though, in comparison to other boxes that have been running ubuntu on, this is a pretty powerful machine and it cant run compiz :(

thank you! 1 million times over though. if you could figure a way to get it running that would be great to! :P

---

### Post by abn91c on 2008-12-29
> **nubix said:**
> well that worked! gratz to you! pat yourself on the back my friend!! :P i am kind of disapointed that i cant run compiz though, in comparison to other boxes that have been running ubuntu on, this is a pretty powerful machine and it cant run compiz :(

thank you! 1 million times over though. if you could figure a way to get it running that would be great to! :P
You are welcome:D, I have the same model Dell, if you want to see it fly upgrade the RAM to at least 1.5 gig. That is what i have. In case you wondering why no compiz, its the intel 845 seres video card, its not compatible with compiz in 8.10

---

### Post by overdrank on 2008-12-29
Threads merged :)

---

