---
title: "Can I get a list of packages that I've installed?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-04
I have changed from my one primary computer to another and when I went to a tutorial, I found that "Oh, yeah, I have to install programs and/or packages to play the videos-to see AND hear them.  I have no sound.

I guess, I think if I can get the list of what I used to have that I will install them and GET sound.

---

### Post by samantha_ on 2010-02-04
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by Enigmapond on 2010-02-04
```
dpkg -l
``` (that's a small L not an i) This will give you a listing of installed packages.
****

---

### Post by Chris Edgell on 2010-02-04
Oh, samantha, I didn't know how great your thread would look to me until I went to the code given by Enigmaposd.  No offfense.  Once I saw THAT list of all that is installed I knew I couldn't even begin with that!  So it's an especial thanks for that thread, Samantha.

---

### Post by Orion8 on 2010-02-04
I note the new "Ubuntu Software Center" lets you do this too.  Open it up and select the "installed software" tab...  Normally I use Synaptic or a terminal shell so I just figured this out!  I think its a nice feature.

Edit: This method only shows installed programs, not libraries or packages per se.  Still, very hand to see what you have.

---

### Post by grobar87 on 2010-02-04
where is installed firefox in ubuntu?
in home .mozilla?
tnx :)

---

### Post by Chris Edgell on 2010-02-04
grobar87,

Do you know how to get to Synaptic Package Manager?

Applications > System > Synaptic Package Manager  shown in the first screenshot.

When you click that you will see the Package Manager, in the search box type Firefox.

You'll probably get another small window, type Firefox again... (see 2nd screenshot)

Tick the box and you'll get a window where it says "Install", it will probably show you the other apps that are related.  They will be installed as a package when you go to the top and click "Apply".

You may go through all the steps and not apply.  Maybe you want to wait and see if someone else tells you something else about this.  

You may go ov

---

### Post by drzoo2 on 2010-02-05
> **Enigmapond said:**
> ```
dpkg -l
``` (that's a small L not an i) This will give you a listing of installed packages.
****

Just to expand on this a little, add the standard out redirector and put it in a file.

like...

```
dpkg -l > listofpackages
```

This will create a file in your path that you can open with gedit.

z

Note this is all packages.

---

### Post by tom.swartz07 on 2010-02-05
> **drzoo2 said:**
> Just to expand on this a little, add the standard out redirector and put it in a file.

like...

```
dpkg -l > listofpackages
```

This will create a file in your path that you can open with gedit.

z

Note this is all packages.

+1 

I was going to suggest something like this. It makes it quick, simple and easy. Nice.

Dont forget the restore command (as highlighted in an earlier post) ```
dpkg --set-selections < listofpackages
```

---

