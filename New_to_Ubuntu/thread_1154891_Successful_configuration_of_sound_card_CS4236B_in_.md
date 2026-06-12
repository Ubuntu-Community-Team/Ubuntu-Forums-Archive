---
title: "Successful configuration of sound card CS4236B in Ubuntu Jaunty"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by t_k_majumdar on 2009-05-10
Hi - 

I was unable to get sound in my old Dell Optiplex GX1 computer with on-board sound card CS4236B after loading Linux distros like OpenSUSE 11.1 and Ububtu 8.10. In absence of sound one can not use an OS, so I searched for solution frantically through Google, OpenSUSE and Ubuntu Forums. Finally, the problem was solved after installation of Ubuntu 9.04 Jaunty Jackalope and few tweakings learned by previous searches. I express my heartiest thanks to all who tried to help me directly by replying to my posts or indirectly by publishing related posts from which I learned. Lastly thanks to Jaunty developers. 

I am giving here a brief account of how exactly the problem was solved.

Step 1. After installation of Ubuntu 9.04, I checked whether the sound card was detected or not by : Applications > Accessories > Terminal > lsmod. It was not.

Step 2. Added "snd-cs4236" in the file /etc/modules/ by : Applications > Accessories > Terminal >  "sudo gedit /etc/modules/. Appended the line, saved, closed and rebooted.

Step 3. Checked again whether the sound card was detected now by : Applications > Accessories > Terminal > lsmod. It was now detected.

Step 4.  Now checked whether the sound testing could be done successfully by : System > Accessories > Preferences > sound > clicking first 3 test buttons. No sound heard.

Step 5. Added the user name of my computer in the file "/etc/group" by : Applications > Accessories > Terminal > sudo sh > (prompt changed to #) grep 'audio' /etc/group. I got output : audio:x:29:pulse.Opened the file by : nano /etc/group > navigated down to find the line "audio:x:29:pulse" > replaced "pulse" by the user name of the computer. [Tips : The user name is also present at the end of lines like "adm:x:4:user name", "dialout:x:20:user name", "cdrom:x:24:user name"] > ^O, Enter, ^X.Rebooted.

Step 6.  Rechecked whether the sound testing could be done successfully by : System > Accessories > Preferences > sound > clicking first 3 test buttons. No sound still.

Step 7. Changed default devices in all sound preferences to "OSS - Open sound system" and device to "CS4236B(OSS mixer)" by System > Accessories > Preferences > sound.

Step 8. Changed default device in Volume control to "CS4236B(OSS mixer)" by Right-clicking the volume control icon on the top of the task bar. Slided the three bars to the topmost positions and finally clicked any of the three speaker icons present in the bottom with a red mark to unmark it.

Step 9.  Checked now whether the sound could be heard by : System > Accessories > Preferences > sound > clicking first 3 test buttons. A high-pitched loud sound greeted me. What a sigh of relief! But I was unable to play mp3 songs or movies.

Step 10. Enabled the medibuntu repositories by: Applications > Accessories > Terminal > sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Step 11. Installed non-free-codecs by : Applications > Accessories > Terminal > sudo apt-get install non-free-codecs

Step 12.Installed more codecs, DVD support, VLC and mplayer by: Applications > Accessories > Terminal > sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder. The last three steps as per guidelines of "Eva's useful guide to Ubuntu 9.04" [http://www.johannes-eva.net/index.php?page=2009_04_useful_ubuntu_guide_jaunty](http://www.johannes-eva.net/index.php?page=2009_04_useful_ubuntu_guide_jaunty).

Now I can play songs and movies. The sound system is working perfectly and sweetly.

---

### Post by MontelEdwards on 2009-05-15
This should be moved to Tutorials & Tips

---

### Post by t_k_majumdar on 2009-05-18
Thanks m.deonte for your comment. 
I shall be pleased if my experience helps anyone. However, should I move it to Tutorials & Tips as you suggested or it should be done by webmaster? 
And if I have to move it how should I do it?

---

### Post by MontelEdwards on 2009-05-19
No, you just post the thread there.
 They have to be approved by staff or admin before they can be seen by public. They usually take about 2 days to approve. I guess I should of clarified that before.

---

