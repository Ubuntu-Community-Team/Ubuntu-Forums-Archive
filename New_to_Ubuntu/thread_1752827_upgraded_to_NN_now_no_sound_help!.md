---
title: "upgraded to NN now no sound help!"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Indyspair on 2011-05-08
I have upgraded (why I bothered now I dont know) and have no sound though all my checks say everything is fine, both headphones and main speakers just not doing a thing. Can anyone please help, I am not a computer geek and do not know how to compile etc (nor do I want to particularly) I am just a keyboard user.
The only clue I have is at the upgrade start I briefly saw a screen trhat said that 17 applications were unsupported but that they could be updated through (?) afterwards, help here may be needed as well!
Thanks :confused::confused::confused:

---

### Post by jramshu on 2011-05-08
Open a terminal: ctrl+alt+t
Enter this:
```
pulseaudio --version
```
The above will tell you if the audio server is installed and what version. If it's not then the upgrade may have removed it.

---

### Post by Indyspair on 2011-05-08
pulseaudio 0.9.22-24-g67d18
is the answer????
thanks for your swift reply by the way, but this means absoloootly naf all to me!

---

### Post by Hedgehog1 on 2011-05-08
In case you are using NVidia and want the run 'sound over HDMI': [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294").


***The Hedge***

:KS

---

### Post by Indyspair on 2011-05-08
Have just tried to do the system check, it said the audio device was HDA-Intel_HDA ATI SB (and) HDA ATI SB @Oxfeb4000 Irq 16.
It failed all system sound tests!
However when starting up I get a sound bleep from the Asus first screen, after that the silence is complete!
Followed the advice on another thread and made a new user account but no difference, I have spent all day on this so far and I cannot access my audio files of my lectures from uni and I should be revising for the exams (law) in a weeks time, I am stuffed!!!!:confused:

---

### Post by jramshu on 2011-05-09
You can try this below in a terminal and see if it will update the apps that weren't updated. You can also try and update using the update manager(System>Administration>Update Manager) Watch to see if it shows that it is going to remove pulseaudio, if so let us know.

```
sudo apt-get update && sudo apt-get upgrade
```
Then this:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

