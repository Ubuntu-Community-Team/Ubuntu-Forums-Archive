---
title: "PC to TV via HDMI = no sound"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by maryalesia on 2011-01-08
When I connect my pc to my TV with an HDMI chord, I am unable to get the sound to come out of my TV speakers (it does come out of the pc speakers, though).

I have tried switching the audio hardware to HDMI output on the PC and making sure that HDMI input is selected as the audio source in the TV. All that succeeds in doing is turning off the sound altogether. 

This wasn't a problem before, because I had this really nifty altec lansing USB speaker that kicked some USB speaker butt. My rabbit chewed through the wire. 

And so I have returned the the forums. :D

Any ideas?

---

### Post by Kasami on 2011-01-09
What graphics card are you using? When I tried to run sound through HDMI to the television I had to install the proprietary drivers for my graphics card. Hope that helps =]

---

### Post by maryalesia on 2011-01-09
> **Kasami said:**
> What graphics card are you using? When I tried to run sound through HDMI to the television I had to install the proprietary drivers for my graphics card. Hope that helps =]

 Nvidia Geforce 9800M GTS. I have the proprietary drivers installed. :confused:

---

### Post by Kasami on 2011-01-09
Have you tried this solution?

[http://ubuntuforums.org/showthread.php?t=1173022](http://ubuntuforums.org/showthread.php?t=1173022)

---

### Post by maryalesia on 2011-01-09
> **Kasami said:**
> Have you tried this solution?

[http://ubuntuforums.org/showthread.php?t=1173022](http://ubuntuforums.org/showthread.php?t=1173022)

No, but it should be noted that I couldn't even if I wanted to because I like me my graphical user interface. Command line? What command line?

Thanks, though. :)

---

### Post by Kasami on 2011-01-09
Command line is what you are using when you open a terminal. Applications > Accessories > Terminal.

---

### Post by maryalesia on 2011-01-09
> **Kasami said:**
> Command line is what you are using when you open a terminal. Applications > Accessories > Terminal.

I know what it is ... I just would rather not use it. I don't know bash and I don't understand what I read in that thread. I really do appreciate you trying to help, though.

---

### Post by VincentLaw on 2011-02-19
> **maryalesia said:**
> I know what it is ... I just would rather not use it. I don't know bash and I don't understand what I read in that thread. I really do appreciate you trying to help, though.

I had the same issue and didn't find any other solution than opening a terminal :biggrin:
In case of, here is the solution that worked for me :
* Open a terminal
* Type in "alsamixer"
You got someting like this :
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                 F1:  Help               &#9474;
&#9474; Chip: Nvidia MCP77/78 HDMI                                      F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                        F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF 1 [Off]                                            Esc: Exit               &#9474;
&#9474;                                                                                         &#9474;
&#9474;                                                                                         &#9474;
&#9474;               &#9484;&#9472;&#9472;&#9488;                                                           &#9484;&#9472;&#9472;&#9488;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;    Mic In   Mic In    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;   Digital    &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;       &#9474;
&#9474;      &#9474;OO&#9474;                                &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;MM&#9474;     &#9474;OO&#9474;       &#9474;
&#9474;      &#9492;&#9472;&#9472;&#9496;                                &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;       &#9474;
&#9474;             100<>100                                                          0         &#9474;
&#9474;    Bass Spe   PCM    Front Mi Mic Jack  S/PDIF  S/PDIF D S/PDIF P<S/PDIF 1>  Beep       &#9474;
&#9474;                                                                                         &#9474;
&#9474;                                                                                         &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```As you can see, my output "S/PDIF 1" is tagged "MM" for **mute**

* Put the cursor on it and hit "M". You'll see "[Off]" disapearing on the left upper side of the screen
* Sound is now ON !
* ESC to exit

Hope this will help

---

### Post by maryalesia on 2011-02-26
thanks for the help! I did what you said, and was pleased that it didn't involve editing a bunch of code, which frightens me to no end. (I know just enough about the terminal to really screw things up). 

Question, though:

do any of those sound card options have anything to do with a USB speaker? Because I use one, but my computer keeps randomly defaulting back to the internal speakers. Sound still comes out of the USB speaker, but volume controls no longer work on it. :confused:

---

### Post by Praet0rian on 2012-04-21
> **VincentLaw said:**
> I had the same issue and didn't find any other solution than opening a terminal :biggrin:
In case of, here is the solution that worked for me :
* Open a terminal
* Type in "alsamixer"
You got someting like this :
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                 F1:  Help               &#9474;
&#9474; Chip: Nvidia MCP77/78 HDMI                                      F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                        F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF 1 [Off]                                            Esc: Exit               &#9474;
&#9474;                                                                                         &#9474;
&#9474;                                                                                         &#9474;
&#9474;               &#9484;&#9472;&#9472;&#9488;                                                           &#9484;&#9472;&#9472;&#9488;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
<               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;               &#9474;&#9618;&#9618;&#9474;                                                           &#9474;  &#9474;       &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;    Mic In   Mic In    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;   Digital    &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;       &#9474;
&#9474;      &#9474;OO&#9474;                                &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;MM&#9474;     &#9474;OO&#9474;       &#9474;
&#9474;      &#9492;&#9472;&#9472;&#9496;                                &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;       &#9474;
&#9474;             100<>100                                                          0         &#9474;
&#9474;    Bass Spe   PCM    Front Mi Mic Jack  S/PDIF  S/PDIF D S/PDIF P<S/PDIF 1>  Beep       &#9474;
&#9474;                                                                                         &#9474;
&#9474;                                                                                         &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```As you can see, my output "S/PDIF 1" is tagged "MM" for **mute**

* Put the cursor on it and hit "M". You'll see "[Off]" disapearing on the left upper side of the screen
* Sound is now ON !
* ESC to exit

Hope this will help

I mean.. thanks alot for this! And I thank to myself as well trying this out before typing my fingers off in terminal with other proposed solutions ;)
The S/PDIF 1 was "MM" indeed..

---

