---
title: "Install from .bin 9.10"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by stalkier on 2009-12-05
I am trying to install Savage 2 from a .bin file. I have searched Google and Ubuntu Forums with no luck. I am using Ubuntu 9.10. I am not fluent in CLI so any help would be great. I am not a noob but my 3 second attention span hurts my retention level. :D Thanks

Game site: [http://savage2.com/en/main.php](http://savage2.com/en/main.php)

---

### Post by corncob on 2009-12-05
I don't know anything about Savage2 but what I do with bin files is to put them in my home folder, make them executable:
```
sudo chmod +x whatever.bin
```
and run it.

---

### Post by stalkier on 2009-12-05
> **corncob said:**
> I don't know anything about Savage2 but what I do with bin files is to put them in my home folder, make them executable:
```
sudo chmod +x whatever.bin
```
and run it.

Error:
Could not display "/home/john/Savage2Install-2.1.0.1-x86_64.bin". There is no application installed for bin document files

What to do?

---

### Post by 3rdalbum on 2009-12-05
Run it in the terminal. If it is an installer, it needs to be run as root. So, in the terminal, type 'sudo', press the space bar, and drag the file to the terminal.

---

### Post by stalkier on 2009-12-05
> **3rdalbum said:**
> Run it in the terminal. If it is an installer, it needs to be run as root. So, in the terminal, type 'sudo', press the space bar, and drag the file to the terminal.

```
john@john-desktop:~$ sudo '/home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin'/home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin: 2: Syntax error: "(" unexpected
john@john-desktop:~$
```

---

### Post by Bradj47 on 2009-12-05
> **stalkier said:**
> ```
john@john-desktop:~$ sudo '/home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin'/home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin: 2: Syntax error: "(" unexpected
john@john-desktop:~$
```

That means there's an error in the code at line 2.

---

### Post by stalkier on 2009-12-05
> **Bradj47 said:**
> That means there's an error in the code at line 2.

Can this be corrected? Like opening the bin file with a text editor and deleting the "(" at line 2?

---

### Post by Bradj47 on 2009-12-05
> **stalkier said:**
> Can this be corrected? Like opening the bin file with a text editor and deleting the "(" at line 2?

Every time I opened up a bin file with Solaris (another Unix-like OS), my Terminal locked up and was flooded with seemingly random text and I had to remote-kill it with another machine on the network. I would expect the same results in Ubuntu, but I don't have any experience with bin files on Ubuntu so I'm not sure what would happen. You could try it, but you might have to do a force-kill from another computer (if you have one on the network), or if you don't have one on the network you'll have to shut down your computer by force. If you have more than one Unix computer on the network, you could try it, but if you don't make sure you aren't running anything important. Just to be safe.

---

### Post by stalkier on 2009-12-05
> **Bradj47 said:**
> Every time I opened up a bin file with Solaris (another Unix-like OS), my Terminal locked up and was flooded with seemingly random text and I had to remote-kill it with another machine on the network. I would expect the same results in Ubuntu, but I don't have any experience with bin files on Ubuntu so I'm not sure what would happen. You could try it, but you might have to do a force-kill from another computer (if you have one on the network), or if you don't have one on the network you'll have to shut down your computer by force. If you have more than one Unix computer on the network, you could try it, but if you don't make sure you aren't running anything important. Just to be safe.

Thanks for the info. I tried using gedit to open it. It loaded it then crashed. I am redownloading the 32bit version this time to see if I can get that one to work. If not, then oh well. Guess I could try running the Windows exe in WINE.

---

### Post by RJ12 on 2009-12-05
> **Bradj47 said:**
> Every time I opened up a bin file with Solaris (another Unix-like OS), my Terminal locked up and was flooded with seemingly random text and I had to remote-kill it with another machine on the network. I would expect the same results in Ubuntu, but I don't have any experience with bin files on Ubuntu so I'm not sure what would happen. You could try it, but you might have to do a force-kill from another computer (if you have one on the network), or if you don't have one on the network you'll have to shut down your computer by force. If you have more than one Unix computer on the network, you could try it, but if you don't make sure you aren't running anything important. Just to be safe.

Well you can also use the ultimate keyboard shortcut that is suppose to safely shutdown/restart your system without corruption
hold down Alt+PrtScrn while slowly pressing these keys in this order REISUB

---

### Post by corncob on 2009-12-06
> **stalkier said:**
> ```
john@john-desktop:~$ sudo '/home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin'/home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin: 2: Syntax error: "(" unexpected
john@john-desktop:~$
```

Looks to me like its there twice.  Did you ever change it to an executable?  Since its on your desktop you'd type
```
sudo chmod +x /home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin
```
into the terminal.  Then run it:
```
sudo /home/john/Desktop/Savage2Install-2.1.0.1-x86_64.bin
```

---

### Post by Bradj47 on 2009-12-06
> **RJ12 said:**
> Well you can also use the ultimate keyboard shortcut that is suppose to safely shutdown/restart your system without corruption
hold down Alt+PrtScrn while slowly pressing these keys in this order REISUB

Then there's also the keyboard shortcut that opens a Terminal, Crtl+Alt+F1, then kill the process using that... I forgot Ubuntu had that feature. :P

---

