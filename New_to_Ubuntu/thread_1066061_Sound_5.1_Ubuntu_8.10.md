---
title: "Sound 5.1 Ubuntu 8.10"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by itapragh on 2009-02-10
Hello everyone, I am new last week I change my OS from WXP to Ubuntu 8.10 64 bits and I am getting used to it, I haven't checked everything that ubuntu offers because I am trying to make my home thater work, 
When I used Xp I just plugged the green, pink, and orange plugs with the plugs that came with my creative home theater and everything sounded good but with ubuntu just appears to function the one that es conected to the central plug (which controls de 2 rear speakers)
I dont know what to do I have tryied everything that I have found in the forums and nothing works, because my soundcard its not a 5.1 card it has the 3 output that comes with the intel motherboard.. 
Please help!!!

---

### Post by DiegoBretti on 2009-03-03
> **itapragh said:**
> Hello everyone, I am new last week I change my OS from WXP to Ubuntu 8.10 64 bits and I am getting used to it, I haven't checked everything that ubuntu offers because I am trying to make my home thater work, 
When I used Xp I just plugged the green, pink, and orange plugs with the plugs that came with my creative home theater and everything sounded good but with ubuntu just appears to function the one that es conected to the central plug (which controls de 2 rear speakers)
I dont know what to do I have tryied everything that I have found in the forums and nothing works, because my soundcard its not a 5.1 card it has the 3 output that comes with the intel motherboard.. 
Please help!!!


To fix 2.0 to 5.1 put this:

=> sudo gedit /etc/pulse/daemon.conf

Go down to the line that says "default-sample-channels = 2"
Change it so it looks like the following:
"default-sample-channels = 6"
Save and exit.

After you reboot, test your sound using:

=> speaker-test -Dplug:surround51 -c6 -l1 -twav

---

### Post by DiegoBretti on 2009-03-23
itapragh, It works?

---

### Post by gRinD on 2009-03-23
Hello there. I don't know about the original poster, but I just tried what you suggested and it didn't work for me. Only the 2 front speakers gave me the test sound after the reboot.

---

### Post by DiegoBretti on 2009-03-30
> **gRinD said:**
> Hello there. I don't know about the original poster, but I just tried what you suggested and it didn't work for me. Only the 2 front speakers gave me the test sound after the reboot.

To fix this problem install the following commands:

=> sudo killall pulseaudio
=> sudo alsa force-reload

and then go to "System > Preferences > Sound" and change everything to ALSA.

---

### Post by eliotv10 on 2009-10-03
Hello,
I just installed ubuntu and had exactly the same problem.I feel sorry that your problem didn't solved quickly,but there i found a sure solution.

First of all,press your sound icon,placed in the bar right left.Secondly,press the button "check sound volume"or somewhat(i cannot tell you exactly because my ubuntu is at greek).Thirdly,go at preferences,and cheack _ONLY_ the choices i refer:

Central
PCM
Front
Surround
Center
LFE
-The thing after the choice "Side",i don't know to say it in english
MIcrophone(if you go tone)

Press close,and set every bar to its full power.Tell me if you dodn't understand or didn't worked for you.



(You should do also what people told you to do so above,in addition with this.)

---

