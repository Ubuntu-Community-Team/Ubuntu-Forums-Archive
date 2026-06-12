---
title: "PLease help me to un-install flashplayer 10.1 beta"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by nikef on 2010-03-05
Hi all 

I am trying to un-install flashplayer 10.1 beta

Every time i ask for it to be removed i come up against an error ,even doing in terminal will not remove it :mad:

I am trying to install other sofware but it will not allow me to do this because it can not remove the flashplayer 

Thanks for any help

---

### Post by swoll1980 on 2010-03-05
> **nikef said:**
> Hi all 

I am trying to un-install flashplayer 10.1 beta

Every time i ask for it to be removed i come up against an error ,even doing in terminal will not remove it :mad:

I am trying to install other sofware but it will not allow me to do this because it can not remove the flashplayer 

Thanks for any help

How did you install it?

---

### Post by nikef on 2010-03-05
Hi and thanks

I downloaded it from here 

   [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

and extracted it,but there was a problem while extracting it ,so i kept on trying and now i can not get rid of it

---

### Post by ubudog on 2010-03-05
Open a terminal and type: ```
sudo apt-get remove flashplugin-nonfree
``` that should remove it even though you got it from the website.

---

### Post by nikef on 2010-03-05
> **ubudog said:**
> Open a terminal and type: ```
sudo apt-get remove flashplugin-nonfree
``` that should remove it even though you got it from the website.

HI and thanks 

I got this error code  

Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ubudog on 2010-03-05
Type ```
sudo dpkg --reconfigure -a && sudo apt-get remove flashplugin-nonfree
``` That should do it.

---

### Post by nikef on 2010-03-05
> **ubudog said:**
> Type ```
sudo dpkg --reconfigure -a && sudo apt-get remove flashplugin-nonfree
``` That should do it.

Sorry to be a pain but this is what i got 

dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by swoll1980 on 2010-03-05
> **nikef said:**
> Sorry to be a pain but this is what i got 

dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

leave the "re" out it's configure not reconfigure.
```
sudo dpkg --configure -a
```

---

### Post by nikef on 2010-03-05
> **swoll1980 said:**
> leave the "re" out it's configure not reconfigure.
```
sudo dpkg --configure -a
```

Thank you 
This is what i did 

sudo dpkg --configure -a && sudo apt-get remove flashplugin-nonfree

And here is the error 

Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ubudog on 2010-03-05
> **swoll1980 said:**
> leave the "re" out it's configure not reconfigure.
```
sudo dpkg --configure -a
```

Yeah, sorry about that.

---

### Post by nikef on 2010-03-05
Still need help if any1 can help thanks

---

### Post by marshmallow1304 on 2010-03-05
> **nikef said:**
> I downloaded it from here 

   [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

and extracted it,but there was a problem while extracting it ,so i kept on trying and now i can not get rid of it

What did you do after downloading it?  That's not an installer; it only works if you copy libflashplayer.so to where Firefox can get it.

---

### Post by sandyd on 2010-03-05
see sig.
remove button will kill all versions of flash that exist on your system.
it **should** also fix the dpkg error.

---

### Post by nikef on 2010-03-06
> **marshmallow1304 said:**
> What did you do after downloading it?  That's not an installer; it only works if you copy libflashplayer.so to where Firefox can get it.

Thanks for replying

Yes that is what i did i copied it into firefox so i could play Yoville on face book and this works great so i do need this 

I did a lot of installing different  flashplayers trying to get My other firefox to work with the normal flash ,but they would not extract so i sent them to recycle bin 
I also enable the restricted-extras packages
Flashplayer 10.1 beta is in the synaptic package manager and it will not un-install 

I tried to install Frostwire and thats where i get the error it can not un-install the flashplayer beta

Now i know i can have both as i have this setup on my laptop

I just can not understand why its not working

---

### Post by wojox on 2010-03-06
Try this:

```

#Remove Flash
# Deletes a troublesome config file
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
# Force-reconfigures adobe-flashplugin
sudo dpkg-reconfigure adobe-flashplugin --force
# Force-removes adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin
# Installs flashplayer the easy way
sudo apt-get install flashplugin-nonfree

```

---

### Post by nikef on 2010-03-06
> **carlee said:**
> see sig.
remove button will kill all versions of flash that exist on your system.
it **should** also fix the dpkg error.

Thanks for replying Carlee 

I have left you a post in your post .

---

