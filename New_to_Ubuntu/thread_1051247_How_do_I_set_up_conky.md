---
title: "How do I set up conky?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Stalker72 on 2009-01-26
I've read through a guide on how to setup Conky, to no avail. I need some extremely simple steps to follow. I use Kubuntu 8.10.

Thanks,

Stalker72

---

### Post by cdtech on 2009-01-26
See this thread:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by billgoldberg on 2009-01-26
I've written a guide on how to start with conky.

First install conky.

"sudo apt-get install conky"

Then in your home folder, create a file called 

.conkyrc

Don't forget the dot before conkyrc.

Press "ctrl+h" to view the newly created file.

After that, follow my guide:

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/](http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/)

I've tried to explain the basics as simple as I could.

---

### Post by waspbr on 2009-01-26
personally I have never got around to setting it up, conky is supposed to be a geek tool, it takes a great deal of patience to set up. 

I was going to check out this link to do that whenever I have time
[http://maketecheasier.com/how-to-create-a-minimal-and-beautiful-desktop-with-conky/2008/10/30]("http://maketecheasier.com/how-to-create-a-minimal-and-beautiful-desktop-with-conky/2008/10/30")

---

### Post by Stalker72 on 2009-01-26
What kind of file do I create?

Stalker72

---

### Post by Sub101 on 2009-01-26
In your home directory there should be a file called ".conkyrc". That is the file you need to edit.

---

### Post by billgoldberg on 2009-01-26
> **Stalker72 said:**
> What kind of file do I create?

Stalker72

Just a normal text file, call it .conkyrc.

If you have already run conky once before, it could already be there.

Just delete the content and start again.

Tip: use a terminal to start and stop conky.

That will make it easy to quickly see the changes made to conky (save it first or you won't see the changes).

In a terminal use

```
conky
```

to start conky

and

```
killall conky
```

to stop it.

---

### Post by Stalker72 on 2009-01-26
> **billgoldberg said:**
> Press "ctrl+h" to view the newly created file.

It doesn't seem like Ctrl+H works in Dolphin.

Stalker72

---

### Post by billgoldberg on 2009-01-26
> **Stalker72 said:**
> It doesn't seem like Ctrl+H works in Dolphin.

Stalker72

Oh, in one of the menu's you should be able to find a "view hidden files" option.

Or you can open the file directly in a text editor.

I presume KDE still uses Kate as a text editor so the command would be

```
kate /home/yourusernamehere/.conkyrc
```

---

### Post by Sub101 on 2009-01-26
Crtl+H is to show the hidden file you created as denoted by the "." so if this does not work for you try looking through the menus to find "view hidden files" or something similar.

---

### Post by Stalker72 on 2009-01-26
When I run "conky" in Terminal, I get the following errors:

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: missing text block in configuration; exiting
```

Stalker72

---

### Post by Sub101 on 2009-01-26
Can you paste your .conkyrc file?

---

### Post by Sub101 on 2009-01-26
This should solve the issue.

[http://ubuntuforums.org/showthread.php?t=798139]("http://ubuntuforums.org/showthread.php?t=798139")

---

