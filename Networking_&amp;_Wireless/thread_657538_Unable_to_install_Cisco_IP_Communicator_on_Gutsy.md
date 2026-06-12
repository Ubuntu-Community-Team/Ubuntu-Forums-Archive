---
title: "Unable to install Cisco IP Communicator on Gutsy"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by thefutoneng on 2008-01-03
I am trying to install Cisco IP communicator with wine and I get the following message:

```

rob@underwearless:~$ msiexec /i ciscoipcommunicatorsetup.msi 
fixme:msi:MSI_OpenDatabaseW open failed r = 8003001e for L"C:\\windows\\temp\\msi226.tmp"
rob@underwearless:~$ uname -a
Linux underwearless 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
rob@underwearless:~$ wine --version
wine-0.9.52

```

WineHQ identified a bug (7983) to go along with error but I couldn't find any information on how to remedy it.  Any help is much appreciated.

---

### Post by thefutoneng on 2008-01-07
I was able to get my hands on IP communicator that was a exe so my previous problem is gone.  I was able to install it without any problems at all.  Now I'm unable to get the app to register with Call Manager at all.  After configuring the TFTP servers the app crashes.

See attached for console output.

---

### Post by fgimenez on 2008-01-12
Where did you get the .exe file that worked ?
Do you still have it ? Can you share it ?
Did you copy any .dll files to make it work ?

Thanks

---

### Post by thefutoneng on 2008-01-13
You can download it from the Cisco website.  I found it by poking around there.  Any one have any clue why it's crashing?

---

### Post by fgimenez on 2008-01-13
I've found the installer for version 2.1.1.0 and got it working.

From your error log you are missing the "winhttp.dll" file.
Copy it from a windows to the system32 directory under your wine fake C drive.
You may need to set is on winecfg also.
With that DLL I was able to start cisco IP communicator but I'm having some issues with the audio.

---

### Post by thefutoneng on 2008-01-14
Thanks, it didn't crash but now it gets stuck on "Installing CDP"

Here is the console output:

```

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:msg:pack_message msg 7f (WM_GETICON) not supported yet
fixme:msg:pack_message msg 7f (WM_GETICON) not supported yet
fixme:msg:pack_message msg 7f (WM_GETICON) not supported yet
fixme:msg:pack_message msg 7f (WM_GETICON) not supported yet
fixme:imm:ImmReleaseContext (0x3005e, 0x1334c8): stub
Error 12006 has occurred.
fixme:setupapi:SetupDiGetINFClassA "c:\\Program Files\\Common Files\\Cisco Systems\\Media Driver\\cpmt.inf" 0x7baeb098 0x7baeac20 1024 (nil)
fixme:setupapi:SetupDiGetINFClassA "c:\\Program Files\\Common Files\\Cisco Systems\\Media Driver\\cpmt.inf" 0x7baeb430 0x7baeafe4 1024 (nil)
fixme:setupapi:SetupDiGetINFClassA "C:\\Program Files\\Cisco Systems\\Cisco IP Communicator\\CdpPacket.inf" 0x1938900 0x7baeb540 1024 (nil)
Error 12006 has occurred.
fixme:setupapi:SetupDiGetINFClassA "C:\\Program Files\\Cisco Systems\\Cisco IP Communicator\\CdpPacket.inf" 0x1938900 0x7baeb290 1024 (nil)
fixme:setupapi:SetupDiGetINFClassA "C:\\Program Files\\Cisco Systems\\Cisco IP Communicator\\CdpPacket.inf" 0x1938900 0x7baeb290 1024 (nil)
Error 12006 has occurred.


```

I'm guessing from the first error message I'm going to have problems with audio as well once it fully launches.

---

### Post by fgimenez on 2008-01-15
Try Cisco IP Comm. version 2.1.1.0
I had the CDP issue with 2.0.x.x versions but with 2.1.1.0 I was able to start it but without audio

---

### Post by thefutoneng on 2008-01-15
Thanks,  I'll give it a shot later today and let you know how I make out.

---

### Post by thefutoneng on 2008-01-15
I seem to be seeing the same behavior.  2.1.1 installed flawlessly but I get the following message when launching the app:

[I]'Default Windows Audio Device' is either missing or not connected properly.  Please reconnect it and select OK.
To select a different device using Tuning Wizard, select Cancel.[/I]

If I hit cancel to launch Tuning Wizard, Tuning Wizard gives the following complaint:

*There are no compatible sound devices installed on this computer.  Please click 'OK' to exit.*

Any idea how to change audio settings in Wine?

---

### Post by fgimenez on 2008-01-16
Use "winecfg" to configure WINE audio.

---

### Post by thefutoneng on 2008-01-17
I tried configuring winecfg to use ALSA as that is what i setup my plantronics headset to use but to no avail.  I still get the same errors message.

---

### Post by fgimenez on 2008-01-18
we are both stuck at the same place then :(

---

### Post by thefutoneng on 2008-02-25
fgimenez, any luck?  I've tried configuring wine to use ALSA and OSS with no luck.  Same symptoms when trying to launch CIPC.

---

### Post by Kablooie!! on 2008-05-06
Hi all,

I was just wondering if anyone has sorted this out yet.  I'd really like to be able to run the IP Communicator on my Ubuntu machine.

Thanks!
Grant

---

### Post by thefutoneng on 2008-05-06
I haven't had any luck

---

### Post by h4ckluserr on 2008-05-08
can you manually set it to dsp1? I had this same issue with Teamspeak, though it is a native app.. I could not get any voice to go through until I set it to use that device.

---

