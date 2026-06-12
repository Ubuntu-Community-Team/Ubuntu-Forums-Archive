---
title: "configuring a DCP-110C scanner"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by MFoxx on 2011-02-27
[SIZE=2]Hello,  wonderful 'citizens' of the Forum 'City'! 
Well, the fact is that I can't get my DCP-110C scanner working. I've managed to download drivers but I have a problem with configuring the scanner. I don't understand how should I write this command:
[/SIZE]   	 	 	 	p { margin-bottom: 0.08in; }  [SIZE=2][COLOR=Purple]sudo brsaneconfig2 -a name=BRSCANNER model=MFC-425CN ip=10.0.0.15
(of course the name model and ip are user specific). [COLOR=Black](Originally posted by ipa)[/COLOR]
[/COLOR][/SIZE]
[SIZE=2]1)** In other words what should I write for '_*[COLOR=Blue]a name[/COLOR]'*_? Should I write "DCP-110C"?**[/SIZE]
[SIZE=2]**2) And another thing,  I'm absolutely baffled by  '[COLOR=Blue]ip[/COLOR]****'? What is it?  How and where can I find an 'ip' for my scanner?**[/SIZE]
[SIZE=2]I'll be thankful for any ideas[/SIZE]**[SIZE=2].[/SIZE]**
PS I've already read some threads. (Hedgehog helped me to find them) but I'm too 'green' to understand all these things.

---

### Post by Jose Catre-Vandis on 2011-02-27
Is it a network scanner - e.g. plugged into the network with ethernet, or direct to a PC with USB? If the latter you probably don't need an IP address for it. Brother might want you to give it one anyway. Have you followed the Brother instructions on their site, based upon whether you have a network or usb installation?

Name = anything you want but no spaces
Model = DCP-110C

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html)

---

### Post by MFoxx on 2011-02-27
p { margin-bottom: 0.08in; }  [COLOR=#000000][SIZE=4]I am glad to receive your reply, Jose. You r from Britain. Even this fact is very interesting for me because I live in Russia and learn yr beautiful and interesting language.

This scanner supports USB installation. Your advice helped me to write the following command:[/SIZE][/COLOR]
 [COLOR=#800080][SIZE=4]sudo brsaneconfig2 -Brother=BRSCANNER model=DCP-110C [/SIZE][/COLOR] 
 [SIZE=4]I have followed the Brother instructions on their site but failed to get the scanner working in a usual way [/SIZE] 
 [SIZE=4]but then I typed in a terminal[COLOR=#ff0000] sudo xsane[/COLOR] I managed to open Xsane but the machine warned me before opening that it is a kind of risk. I neglected the warning and  scanned  a document successfully .The only problem is that I can't open it and even print the image. The machine, presumably, wants me to open the file as root but how can I do it? The emblem of the file (which looks like a red cross)  means  UNREADABLE. Though my question may sound foolish but I  would like to receive the answer or answers of experienced users. Is it possible to use the Xsane in the way I tried to? [/SIZE] 
 [SIZE=4]I will appreciate any comments on the subject.[/SIZE]
 [SIZE=4]Thanks in advance.[/SIZE]

---

### Post by Jose Catre-Vandis on 2011-02-27
Re running as root see here:
[http://ubuntuforums.org/showthread.php?t=80717](http://ubuntuforums.org/showthread.php?t=80717)
and here:
[http://www.uluga.ubuntuforums.org/showthread.php?p=10216411](http://www.uluga.ubuntuforums.org/showthread.php?p=10216411)

To get at the file you scanned, try running nautilus as root and see if you can access it that way / change permissions on the file

---

### Post by MFoxx on 2011-02-28
Thanks, dear friend! That worked perfectly!
God bless you!
MFoxx

---

### Post by Jose Catre-Vandis on 2011-02-28
My pleasure :)

---

### Post by MFoxx on 2011-11-07
[SIZE=4]I'm using Edubuntu now but can't find "Compiz" on my machine. (I have unity type desktop). Can anyone help me[/SIZE]?

---

