---
title: "No Audio in Ubuntu10.10 64-Bit M2n-AM SE2"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by abhaya_jaiswal on 2011-04-10
I received a desktop-PC from my brother . 
The PC has ASUS [COLOR=Blue]M2N68-AM SE2[/COLOR] motherboard.
In bios setting, I have selected [COLOR=Blue]AC97[/COLOR] (other option was HD Audio), and in [COLOR=Blue]Azila audio[/COLOR], I have selected Enabled
I could successfully install ubuntu[COLOR=Blue]10.10 64-Bit[/COLOR] and am using the same happily.
The only problem I am facing is that audio is not working in this PC.

I  tried to follow "Comprehensive Sound Problem Solutions Guide v0.5e -  http://ubuntuforums.org/showthread.php?t=205449" but could not succeed.

Below are list of things I have tried:-
1. Output of aplay -l (not sure what it stands for)
             [COLOR=Blue]aplay: device_list:235: no soundcards found...[/COLOR]
[COLOR=Black]2. [/COLOR]Output of lspci -v (Not sure whether it's soundcard or is it driver for the hardware)
[COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]   [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]       [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]Subsystem: nVidia Corporation Device cb84
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    Flags: 66MHz, fast devsel, IRQ 23
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    Memory at dfef8000 (32-bit, non-prefetchable) [size=16K]
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    Capabilities: [44] Power Management version 2
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    [/COLOR][/COLOR][COLOR=Black][COLOR=Blue]    Kernel modules: snd-hda-intel
[/COLOR]
The Audio IC on motherboard has the following name:
[COLOR=Blue]    Realtek RTL820ICP 8CA3302 L9070[/COLOR]
        Does it mean that soundcard is from REALTEK and driver is from nVidia??

3. Main Menu -> System -> Preferences -> Sound -> Hardware
    It [COLOR=Blue]does not show any device[/COLOR] in "Device to configure" List

4. [/COLOR][COLOR=Black]Main Menu -> System -> Preferences -> Sound -> Output
    It [COLOR=Blue]Dummy Output Stereo [/COLOR]in "Device for sound output" List

5. I tried gstreamer-properties, but didn't help
       Autodetect: [COLOR=Blue]No sound[/COLOR]
       ALSA[/COLOR][COLOR=Black]: [COLOR=Blue]No sound[/COLOR][/COLOR]
[COLOR=Black]       OSS: [COLOR=Blue]Failed[/COLOR] - Could not open audio device for playback
       OSS Version 4 [COLOR=Blue]Failed[/COLOR][/COLOR][COLOR=Black] - Could not open audio device for playback[/COLOR]
[COLOR=Black]       PulseAudio Sound Server[/COLOR][COLOR=Black]: [COLOR=Blue]No sound[/COLOR][/COLOR]
[COLOR=Black]       Custom[/COLOR][COLOR=Black]: [COLOR=Blue]No sound
[/COLOR]
6. I went to [/COLOR][SIZE=2] [/SIZE][[SIZE=2]http://www.alsa-project.org/[/SIZE]]("http://www.alsa-project.org/alsa-doc/") and searched for soundcard under nVidia.
         after that I ran the following command, but no help.
[COLOR=Blue]         sudo modprobe snd-hda-intel
[/COLOR][COLOR=Blue]         sudo modprobe snd-intel8x0
[/COLOR][COLOR=Blue]         [/COLOR]Added the same in /etc/module also but didn't help

7. [COLOR=Black]At [/COLOR][SIZE=2] [/SIZE][[SIZE=2]http://www.alsa-project.org/[/SIZE]]("http://www.alsa-project.org/alsa-doc/") somehow, I didn't find any entry for ASUS-> M2n68 XXXXX (not sure why).

So,  it would be a great help if you can suggest what else can I try in  order to get the audio working in my PC. Also, it would be helpful if  you can educate me on differences between soundcard/driver and the  physical IC soldered on the motherboard etc.

---

