---
title: "mouse theme wont change...."
date: 2009-02-19
forum: New to Ubuntu
---

### Post by libihero on 2009-02-19
i had my mouse theme on polar cursor for a long time, and i'm trying to change it.  for some reason, it wont change, even when i restart my computer, and the cursor i wanted will only randomly show up.  when i did "killall compiz.real && metacity --replace", it ended up changing to the cursor i wanted.

---

### Post by NESFreak on 2009-02-19
> **libihero said:**
> i had my mouse theme on polar cursor for a long time, and i'm trying to change it.  for some reason, it wont change, even when i restart my computer, and the cursor i wanted will only randomly show up.  when i did "killall compiz.real && metacity --replace", it ended up changing to the cursor i wanted.

what does compiz --replace do?

---

### Post by libihero on 2009-02-19
i was doing it for another reason, but when i did it it ended up working

---

### Post by Metallion on 2009-02-19
Is the mouse theme still there after running compiz? Otherwise try copying your mouse theme directory to ~/.icons and then adding the exact name of your directory in /usr/share/icons/default/index.theme

I'm using the chameleon white theme myself so let me show you how it looks on my computer:

```
metallion@frietjes ~ $ ls .icons/
Chameleon-White-0.5.tar.bz2  [COLOR="Red"]Chameleon-White-Regular-0.5[/COLOR]
Chameleon-White-Large-0.5    Chameleon-White-Small-0.5

metallion@frietjes ~ $ cat /usr/share/icons/default/index.theme 
[Icon Theme]
#Inherits=DMZ-White
[COLOR="Red"]Inherits=Chameleon-White-Regular-0.5[/COLOR]

```

---

### Post by libihero on 2009-02-19
it's not letting me open the index.theme, it says that it's not a folder or something.  is there any way i can uninstall the cursor it keeps switching back to, so that it can only stay the cursor i want?  i'm trying to use Vienna3 instead of Polar Cursor.

---

### Post by libihero on 2009-02-19
bump...
i tried deletin the theme it was stuck on and wouldnt fully transfer from, but now it wont fully transfer from the default theme....

---

### Post by libihero on 2009-02-19
bump...

---

### Post by libihero on 2009-02-20
bump.... :( it wont let my mouse theme completely change anymore...

---

### Post by libihero on 2009-02-22
bump
:(

---

### Post by FAMUgolfer on 2009-02-22
paste your mouse theme in /usr/share/icons

you'll need permission so type "sudo nautilus" in the terminal after you've untarred the file

then just right-click on desktop -> change background --> navigate to and choose your desired mouse theme and presto!!

Hope this works!!

---

### Post by libihero on 2009-02-22
nope still dont work :(
i copied the file from the ~/.icons folder and moved it into the usr/share/icons folder, and then when i chose change background, i opened the index.theme file.  it still didnt change the mouse theme after a logout.

---

### Post by FAMUgolfer on 2009-02-23
your choosing the wrong file.

you don't need the "index.theme" file

download the file again, untar it, and paste the file folder of your desired theme in usr/share/icons

---

### Post by Metallion on 2009-02-23
Hmmm strange since I changed my own theme by using that index.theme file. Can you type this:
```
sudo gedit /usr/share/icons/default/index.theme
```

Now put a # in front of the line that says Inherits and add another line with the exact name of the folder that holds your mouse theme. Like this:

```
Inherits=TheNameOfYourTheme
```

Did you try this already and it didn't work?

---

### Post by libihero on 2009-02-23
i actually fixed it myself lookin through other threads
my compiz was interfering with my mouse theme, so i opened the general options, and low and behold it showed another theme than the one i wanted.  so i typed in the theme i wanted, and it got fixed, no more two cursors randomly switching :)

---

