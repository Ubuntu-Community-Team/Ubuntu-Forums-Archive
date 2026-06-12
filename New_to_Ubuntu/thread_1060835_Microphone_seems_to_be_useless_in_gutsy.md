---
title: "Microphone seems to be useless in gutsy"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Binny88 on 2009-02-05
I use gutsy gibbon and i want to chat in skype,but my microphone doesn't seem to work. It works well in skype for XP:D. It worked quite well in hardy.

Can anyone suggest a solution.

Thanks in advance

---

### Post by arochester on 2009-02-05
The microphone setting for Skype is in Skype.

Open Skype. Click on the "S" button (bottom left)>Options>Sound Devices

I had to Change Sound In and Out to the option with "HW" in it

---

### Post by stando007 on 2009-02-05
PLease help me, because I will get MAD from this!!! Why so many things in ubuntu must be so complicated? By default on System->Preferences->Sound everything is "default" and I can hear sounds from mp3s, videos....
But I cannot hear anything from skype. I tried to change settings in skype from "default" which I do not know why is not working to pulse - worked, or to Intel ICH7 (hw:ICH7,0) for playing sounds and ringing - worked.
But what I have to do to make MIC work?!!!!! When I plug mic into the PC (Dell Optiplex GX620) I can hear it in speakers when unmute it in mixer. But no success with configurong skype/ubuntu sound for making mic work.

People please help me because I am completely lost (doing such thing like making skype call (configuring system, skype) more than 2 hours without success is terrible! On windows it is onlyu installation of skype).

I am not complete newbie in ubuntu, but still have to learn and discover. But when my life will go so hard with linux, I will have to use it only as a server unfortunately (when needed) :( and as a desktop OS stil windows :(

---

### Post by Binny88 on 2009-02-06
Well linux is a bit different from Windows. Windows was built to be extremely user friendly. Any program can be installed in it, well automatically. The programs get an extra dose of pampering from the windows kernel. But this also  increases its security risk. Viruses and malware can be installed automatically without you knowledge and take full control of the system.
In linux viruses would have a more difficult time since a virus would have to check for dependencies  and load the required libraries but this results in little bit less user friendliness.

The problem you are experiencing ( installing & running certain programs properly)will be solved sooner or later when more people starting Linux than windows.Programers will write better programs for linux if the user base increases.

---

### Post by stando007 on 2009-02-06
OK, but what not? One my linux-lover friend would say "do not use such stupid software like skype, it is bad software" :) OK, maybe this is truth, but I have many friends which:
1. are using skype and will not have to switch to any other
2. do not have much technical knowledge to catch they should install and use something else

So I want linux (I like it) but want to have skype there and also want to "have fun" and live in peace with this system :)

For me system (mean desktop home OS) which is stable and secure, but requests 2-3 times more time for configuring and workarounding issues than normal usage is not very useful :(

Anyway, I remember when I first tried some linux distro (I think it was some mandrake linux) it was realy pain when I compare to recent distros (remember only such stupid think like mounting USB mass storage devices had to be done manually...). I think programmers should keep in mind that not all the people think like they do and should make software more friendly :)

But what with my problem with mic in skype? How can I solve it? Anybody helps?

---

### Post by stando007 on 2009-02-06
So, I solved the issue with microphone in Skype. I removed Pulseaudio following this how-to:
[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)

Then in Skype set all devices to "default" and microphone is working :)

But I still have the question what other than "default" devices means? When I swith to any other than default settings I cannot hear audio or getting "Problem with sound capture" error message.

Other than default Skype sound device settings:
Intel ICH7 (hw:ICH7,x)
Intel ICH7 (plughw:ICH7,x)
where x is on my system from 0 till 4
And there is also "headset" and "hdmi" option.

---

