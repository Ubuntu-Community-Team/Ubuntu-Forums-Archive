---
title: "No sound"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by lord raffles on 2009-05-26
HI can anyone help?

just bought a toshiba nb100, it worked fine out of the box and then did a huge update and now there is no sound. am new to ubuntu, have looked at forum and dont really  understand the answers. 
Got the mute sign over the volume control, have tried to open control and get message
no volume control gstreamer plugins found
If anyone can help that would be great, step by step instructions pls, treat me like a dummy!

thank you

---

### Post by aesis05401 on 2009-05-26
Hello, 

I wonder if you have seen this link: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Even if you do not understand all of the instructions, completing the first few steps will help others understand where the problem may be. 

First go to a terminal and type :
```

aplay -l

```

The 'aplay' program is a little utility related to the ALSA driver (Advanced Linux Sound Architecture). By running 'aplay -l' you are asking the program 'aplay' to 'list' the available sound devices.  

If you see your sound device listed here it is a good sign, the link that I have posted above will give you direction from there (like adjusting the alsa-mixer).  

If not, next use the following:
```

sudo lspci -v > devices.052609
less devices.052609

```

The lspci program literally just lists the devices that the OS is seeing - even if they are not performing correctly.  The instructions above will first run 'lspci' with '-v' (tells it to print verbose level of information), and then save the output of the command to a file called devices.<todays-date>.  The second command uses the text reader 'less' to open the file we just created.  

By scrolling through the information in the file devices.052609 you should find a section labeled 'Audio Devices' that will have information related to the sound card.  

If you do not understand the directions provided in the troubleshooting guide I linked to then please post the output of aplay and lspci here so we can take a look at it all.  

P.S. Don't worry about all the stuff at the beginning of the trouble shooting guide, scroll down and start reading where it says: "General Help - Start here if you have no idea why sound is not playing"

---

