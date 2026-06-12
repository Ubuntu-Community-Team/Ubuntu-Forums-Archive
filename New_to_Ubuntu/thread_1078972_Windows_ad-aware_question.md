---
title: "Windows ad-aware question"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-02-23
Now, I'm aware linux is pretty safe from all forms of viruses, ad-aware, and spyware. Though I do have a question.

I was promted to install "VirusScannerInstaller.exe" in a popup simulated to look like a My Computer window, hahaha. Of course that wouldn't even work cause linux doesn't do .exe files, but I cancelled it anyway. But in most ad-aware situations, by the time you find a way to get back to your desktop and get through endless popups asking you to try their virus scan, you already have the attack dug deep into your windows-based computer if you don't have the proper software.

So, if a linux machine is exposed to windows-ad-aware, what happens with the file? Does it just sit on your computer?

---

### Post by sandyd on 2009-02-23
THe only way you can run windows viruses is through a virtual box or WINE, cedega, crossover .etc.etc.etc

the viruses will probably just stay there and make every app inside the particular infected bottle infected.

thats all there is to it

nice question b.t.w. ;)

---

### Post by sandyd on 2009-02-23
> **mattbutsko said:**
> Now, I'm aware linux is pretty safe from all forms of viruses, ad-aware, and spyware. Though I do have a question.

I was promted to install "VirusScannerInstaller.exe" in a popup simulated to look like a My Computer window, hahaha. Of course that wouldn't even work cause linux doesn't do .exe files, but I cancelled it anyway. But in most ad-aware situations, by the time you find a way to get back to your desktop and get through endless popups asking you to try their virus scan, you already have the attack dug deep into your windows-based computer if you don't have the proper software.

So, if a linux machine is exposed to windows-ad-aware, what happens with the file? Does it just sit on your computer?

p.s. the only way to get one of those on linux is to manually run something like Zango.. .etc.etc On the computer, or if your being an idiot and are running web apps like firefox, chrome, IE... through WINE, emulators, that kind of stuff

---

### Post by jerrrys on 2009-02-23
you didnt say what browser your running, but...

[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

[http://noscript.net/](http://noscript.net/)

---

### Post by rafac24 on 2009-02-23
You can never go wrong with AdBlock.

---

### Post by DGortze380 on 2009-02-23
> **mattbutsko said:**
>  what happens with the file? Does it just sit on your computer?

Those type of attacks generally take advantage of a vulnerability in the browser allowing it to download or run remotely. Since your file structure, kernel and programs are entirely different from a windows machine, it's unlikely anything ever even got to your hard drive. If it did, it certainly can not execute.

---

### Post by cybercookie72 on 2009-02-23
what about platform independent code?

does this mean that a keylogger of sometype coded in js or flash cant watch what is happening on the browser?

---

### Post by DGortze380 on 2009-02-24
> **cybercookie72 said:**
> what about platform independent code?

does this mean that a keylogger of sometype coded in js or flash cant watch what is happening on the browser?

platform independent code won't necessarily have full functionality over different platforms. If a javascript for example, executes in mozilla and attempts to edit the registry, or execute in a particular windows directory, nothing will happen, the files/programs/executables the code attempts to utilize don't exist.

I'm not familiar with any spyware utilizing keyloggers .. or for what purpose... they may execute, but again, even if the code is written in a platform independent form, it would need a platform independent method of utilizing that data...

---

### Post by 3rdalbum on 2009-02-24
> **cybercookie72 said:**
> what about platform independent code?

does this mean that a keylogger of sometype coded in js or flash cant watch what is happening on the browser?

Flash cannot be used to interact with the web browser. Flash movies do not have access to any internal browser functions.

Javascript only has access to a limited subset of browser functions, and scripts are sandboxed so they can only access data about the page they are run from. There is such a thing as a "cross-site scripting attack" that breaks out of the sandbox and gets access to information from pages in other frames or tabs, but these are rare, and I'm still not sure they'd be able to record keystrokes.

---

### Post by DGortze380 on 2009-02-24
> **3rdalbum said:**
> Flash cannot be used to interact with the web browser. Flash movies do not have access to any internal browser functions.

Javascript only has access to a limited subset of browser functions, and scripts are sandboxed so they can only access data about the page they are run from. There is such a thing as a "cross-site scripting attack" that breaks out of the sandbox and gets access to information from pages in other frames or tabs, but these are rare, and I'm still not sure they'd be able to record keystrokes.

Essential what I was trying to get at, but said much better. Thanks!

---

### Post by donkyhotay on 2009-02-24
> **u.lover said:**
> It stays in your pc as a guest. No harm. Because linux world doesn't know how to deal with .exe :)

Heh, actually the linux world *does* know how to deal with .exe files... make them incapable of running! (c;

---

