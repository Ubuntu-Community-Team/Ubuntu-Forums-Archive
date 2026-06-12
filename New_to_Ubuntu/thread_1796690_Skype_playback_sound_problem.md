---
title: "Skype playback sound problem"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Old-un on 2011-07-04
I am running Lubuntu 11.04 and still can't get Skype to playback the test call i make while setting up Skype. I have tried to use Sound Recorder as suggested in a post i read but i can't even start Sound Recorder because i get the following message:

Your audio capture settings are invalid. Please correct them with the Sound Preferences under the System Preferences menu. Problem here is i can't find any thing called Sound Preferences?

I did download Gnome-Alsamixer via Synaptic and unmuted everything in sight but i still can't get Sound Recorder to open up?

Could someone help me please.

---

### Post by terrykiwi83 on 2011-07-04
Have you left clicked on the speaker in the taskbar? then gone to sound preferences? I assume your running gnome?

---

### Post by Old-un on 2011-07-04
Hi terrykiwi83

Yes i have right-clicked on the speaker icon on the taskbar but for some reason it is greyed out?

---

### Post by frankbooth on 2011-07-04
A few questions...

**1)** Has Skype ever worked for you? Or is this the first time you try it with Lubuntu? (or any other dist)

**2)** What kind of laptop/soundcard do you use?

---

### Post by frankbooth on 2011-07-04
> **Old-un said:**
> Hi terrykiwi83

Yes i have right-clicked on the speaker icon on the taskbar but for some reason it is greyed out?

He assumed you're using Gnome, but you're running Lubuntu and thus using LXDE.

---

### Post by Zill on 2011-07-04
Old-un:  You could try [volwheel]("https://bbs.archlinux.org/viewtopic.php?id=94434").

Caveat:  I haven't used LXDE so cannot confirm how well Volwheel integrates but it is fine for me with OpenBox.

---

### Post by Old-un on 2011-07-04
Hi frankbooth

Yes i have had Skype work for me but with a different OS. But this is the first time that i have tried to use Skype in Lubuntu.

I tried to find out what sound card i am using by using sudo lshw and in the section multimedia this is the output:

 *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:fe029000-fe0290ff

I hope that helps?

---

### Post by SteveDee on 2011-07-04
> **Old-un said:**
> I am running Lubuntu 11.04 and still can't get Skype to playback the test call i make while setting up Skype....

I am running Skype 2.1.0.81-1 on Lubuntu 11.04.

Open LXTerminal and type:-
```

alsamixer

```
This will launch AlsaMixer (not the Gnome version).
Press F6 to select sound device, and select your camera (assuming this includes your mic)
Set the input level to max using up arrow key.
..now test Skype again.

---

