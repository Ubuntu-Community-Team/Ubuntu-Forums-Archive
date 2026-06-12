---
title: "Installation of adobes Flash player"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Just-me on 2009-11-04
Hi,  I'm an newbie and just got a Question. After Installing Ubuntu 9.1 I tried to install the Flash Player 10 from the Adobe website as an .deb - After downloading the installer starts and stops immediately with this message:  [COLOR=Red]Error: Dependency is not satisfiable: libnspr4-dev[COLOR=Black]
Nothing else.
Any help or advice, please

Thank you!
[/COLOR][/COLOR]

---

### Post by phillw on 2009-11-04
> **Just-me said:**
> Hi,  I'm an newbie and just got a Question. After Installing Ubuntu 9.1 I tried to install the Flash Player 10 from the Adobe website as an .deb - After downloading the installer starts and stops immediately with this message:  [COLOR=Red]Error: Dependency is not satisfiable: libnspr4-dev[COLOR=Black]
Nothing else.
Any help or advice, please

Thank you!
[/COLOR][/COLOR]


Click on   System --> Administration --> Synaptic Package Manager

Enter you pass-word
Type in adobe in the search box
Select adobe flash plugin (click the box)
Select Apply & it'll go do it for you,

Phill.

---

### Post by CharlesA on 2009-11-04
I installed Flash player from the repos after checking "restricted" and "universal" in software sources.

Searched synaptic for "flash"

---

### Post by Just-me on 2009-11-04
Thank you for the response!
Unfortunately it's not working on my computer. as i went to synaptic i gave it my password and startet to search for adobe. I found a plugininstaller for flash, but i could do nothing with it. 

Here is the message:

[COLOR=SandyBrown]Canonical does not provide updates for flashplugin-installer. Some updates may be provided by the Ubuntu community.[/COLOR]

Any further idea?

Thanks for help

edit: the same happens if i search for "flash"

---

### Post by nothingspecial on 2009-11-04
If you have alredy tried to install the .deb first try

```
sudo apt-get install -f
```


Which will usually correct the dependencies.

Alternatively you can type ```
sudo apt-get install ubuntu-resrticted-extras
```

or search for it in synaptic.

That will install flash, java and loads of other funky stuff like media codecs and the like.

---

### Post by m4tic on 2009-11-04
Go to synaptic and click reload, i think the flash installer will auto download from here, if it doesnt search for flash as i'm sure it will be visible now

---

### Post by Just-me on 2009-11-04
Thank you all for your help!  It's solved!  My solution was to give this package the right to write. After this the installation worked. Only the installer asked me to install 2 more packges i found in Synaptics. After installing this 2 packages and updating the Ubuntu itself everything works fine!  Thanks!

---

