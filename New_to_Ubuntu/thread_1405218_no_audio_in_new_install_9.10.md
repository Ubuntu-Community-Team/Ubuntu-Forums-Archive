---
title: "no audio in new install 9.10"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by smithsal on 2010-02-12
I am having trouble with my audio.  I am running ubuntu 9.10 along side of 32 bit windows vista.  When I did my test after the install my sound didn't work.  I believe the sound card it showed was the correct one.  

Detecting your sound device(s):

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0440000 irq 22

When I go to my sound preferences it doesn't show anything under audio hardware though.

I've been looking through the forums but this is my first attempt installing ubuntu, so alot of the things people suggest I am not sure how to do.  Any help you can give me would be greatly appreciated.  If there is more info needed let me know.  Thanks

---

### Post by Dougie187 on 2010-02-12
What kind of test did you do?

Post the output of this from a terminal
```
lshw -c multimedia
```

---

### Post by smithsal on 2010-02-12
The test I did was just the audio test from system testing

sarah@sarah-laptop:~$ lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:d0440000-d0443fff

---

### Post by Dougie187 on 2010-02-12
Well, according to this, your audio device is working fine. I would try playing a song on the internet or something, and make sure you volume is turned on.

The audio test in system testing simply records the users voice (as they talk into a microphone on their system) and then plays that back to them.

This could have three issues I can see.

1. You didn't know you had to talk into a microphone so nothing was recorded and you didn't hear anything played back.

2. Your microphone isn't configured correctly so nothing recorded and you didn't hear anything play back.

3. Your sound card isn't configured correctly and you didn't hear anything played back.

Now, I am guessing the correct one is #2. Because I don't think the microphones are set up correctly by default. Though it gives you instructions on how to do it in that system testing test. Also though, I don't even know if you have a microphone on your computer.

Anyways, I would try something that you know has sound in it first, and then if that doesn't work come back and say "My sound still doesn't work" . But again, make sure your volume is turned up.

---

### Post by smithsal on 2010-02-12
My sound still doesn't work.  I tried playing Internet videos and music from my computer.  I checked that the sound was on.  The audio test I did had a couple different things.  The last one I thought was just checking the sound card but like I said I'm new to ubuntu.  I don't really use my sound a lot and usually have it muted in windows but it is just one of those things that is irritating that it isn't work.  Thank you for trying to help me out.

---

### Post by Jefferythewind on 2010-02-12
I have found that I can "fix" most of my sound problems by messing with the options in the "Sound Preferences" window.  I often have a mic that seems not to work, and I look in the Sound Preferences window and it happens to be muted.  Sorry I haven't any better advice.

---

### Post by smithsal on 2010-02-13
so I am beginning to think it may be a problem with my speaker.  it is reading my sound card right but I don't think it is reading my speakers or mic. All I know for sure about them is that they are realtek high definition.  In windows it looks like there is a background program that runs all the time to make them work.

---

### Post by Loopkno on 2010-02-13
I have the same problem and very similar output from the terminal.

I tried the system test but got nothing out of it.

terminal results

lisa@lisa-laptop:~$ lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:92400000-92403fff

---

### Post by Dougie187 on 2010-02-15
> **Loopkno said:**
> I have the same problem and very similar output from the terminal.

I tried the system test but got nothing out of it.

terminal results

lisa@lisa-laptop:~$ lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:92400000-92403fff


As I said previously. The System Test doesn't play any music or anything unless you have a microphone configured properly. So when you run it it may or may not do anything.

Your best bet is to try something you KNOW works, like an mp3 file or playing something from pandora (though that assumes you know how to set up flash). You could also try playing some internet radio from inside rhythmbox or banshee. You should try playing with the Sound Preferences to make sure that you have it properly configured. 

The output should be simple enough, just make sure it's not muted, and that you volume is up loud enough to hear it. According to the command you typed into the terminal, the system recognized your audio card, and has a driver working with it, so it should be properly functioning. The only issues would be configuration and possibly not having speakers hooked up correctly if it's not a laptop.

---

