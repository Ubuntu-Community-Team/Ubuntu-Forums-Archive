---
title: "Executing .exe files on ubuntu"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Envo on 2010-03-08
I want to execute an .exe file on ubuntu. I tried opening it with 'wine windows program loader' which didn't work. Then I tried writing:

wine ****.exe

on terminal, which gave me:

install Windows version of Mono to run .NET executables.

So, I googled to download Mono, to find that Mono is only available in Ubuntu repositories (which I'm guessing is the software centre). But, I could not find 'Mono' in the software centre (I found 'monodevelop', installed it, but gives me same result in terminal), so I'm stuck here. Can anyone suggest where I can go from here? or is there an easier way of opening .exe file on ubuntu. My ubuntu is 9.10 Karmic Koala. 
Any help would be appreciated.

---

### Post by snowpine on 2010-03-08
Welcome to the forums!

Curious how you expect us to help without telling us the name of the application. :)

Here is a list of applications that work, or don't work, in wine:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

I personally recommend dual booting Windows/Ubuntu, so you can use Windows for Windows apps, and Ubuntu for Linux apps. Good luck! :)

---

### Post by Lunx on 2010-03-08
Don't hold me to this as I'm no expert, but I just had a look through synaptic and I think what you are looking for is mono-complete

[COLOR=Navy]Mono is a platform for running and developing applications based on the
ECMA/ISO Standards. Mono is an open source effort led by Novell.
Mono provides a complete CLR (Common Language Runtime) including compiler and
runtime, which can produce and execute CIL (Common Intermediate Language)
bytecode (aka assemblies), and a class library.

This is a metapackage and pulls in the Mono runtime, development tools and
all libraries.

Install this package if you want to run software for Mono or Microsoft .NET
which you are not installing from a Debian package.

[COLOR=Black]There are quite a few dependancies that will be installed along with that

HTH

[/COLOR][/COLOR]

---

### Post by Envo on 2010-03-08
Thank you all for the reply!
The .exe file I was trying to open is just random executable made by my friend, so you wouldn't know it anyways and it is not on the list in Wine website. :-(
I tried installing mono-complete from synaptic, but it still doesn't work. I guess I will have to use Windows 7.

---

### Post by takisan on 2010-03-08
There is also a program called WINE that you have to add a line to your repositories index (Piece of Cake. go to System>Administration>Software Sources. Once there, you go to the Other Software line, click add, and add this to the apt line. ```
ppa:ubuntu-wine/ppa
```)
From there, you just need to type```
sudo apt-get install wine
```

More information can be found at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by juanoleso on 2010-03-08
> **Envo said:**
> 
install Windows version of Mono to run .NET executables.


I got hung up on this too.  This means you have to download the windows version of Mono [[COLOR="Blue"](click here)[/COLOR]]("http://ftp.novell.com/pub/mono/archive/2.6.1/windows-installer/1/mono-2.6.1-gtksharp-2.12.9-win32-1.exe") and install it in wine.  For instance (and this is just an example, your specific code may be different):

```

>wine ~/downloads/mono-2.6.1-gtksharp-2.12.9-win32-1.exe

```

just follow the dialog to install mono in wine and then try and run your friends program with wine again.

Wine and Mono are far from a complete windows environment, though.  GL with that.

---

### Post by ayadmk on 2010-03-09
how can I get a full pack of wine as deb pack to install it on my Desktop because the apt  command did not work on my PC where I use a portable Modem which has not driver on linux.

---

### Post by MichealH on 2010-03-09
It should be on the archive ftp thing but i dont know the link :(

---

