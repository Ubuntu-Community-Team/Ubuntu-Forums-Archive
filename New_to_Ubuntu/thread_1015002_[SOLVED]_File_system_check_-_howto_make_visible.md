---
title: "[SOLVED] File system check - howto make visible?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by heyup on 2008-12-18
What do I do to make the file system check visible and readable?

The file system check appears as tiny text near bottom of screen and is unreadable. I like to be able to read the file system check.

I'm using Ubuntu Hardy.

---

### Post by hyper_ch on 2008-12-18
you mean the check every 30 boot-ups or so?

---

### Post by heyup on 2008-12-18
> **hyper_ch said:**
> you mean the check every 30 boot-ups or so?

Yes. Isn't that the file system check?

I found out how to alter the time between checks, but I'm trying to find out how to make it visible/readable.

It was visible/readable on Gutsy.

---

### Post by donkyhotay on 2008-12-18
Unless there is a problem you don't really need to worry about that. If you really want to see what it's doing you can go into your menu.1st file and remove the word 'splash' from your default boot options. Of course this removes the entire splash screen and every time you boot up you will get all the various CLI messages your system generates everytime it boots up but are usually in the background.

---

### Post by Elfy on 2008-12-18
> menu.1stl not 1

/boot/grub/menu.lst

If you want to edit it

```
sudo nano /boot/grub/menu.lst
``` to use an editor in terminal, or

```
gksudo gedit /boot/grub/menu.lst
``` for a GUI text editor.

---

### Post by heyup on 2008-12-18
Thanks. 

I thought it might be the /boot/grub/menu.lst file that had to be edited, but wasn't sure.

I'll check out the man pages for grub.

---

### Post by heyup on 2008-12-19
I cannot find anything in grub manual that relates to the file systen check. Nor does the /boot/menu.lst file refer to the file system check.

Grub loads prior to the file system check. I guess the splash screen for the file system check is controlled by some other file.

Anyone know?

---

### Post by Elfy on 2008-12-19
If you remove splash then you will see the file check at the expense of seeing all of the boot procedure.

What is it that you expect to see? Ther's nothing stopping you booting recovery mode and then running a file check from the root prompt.

---

### Post by heyup on 2008-12-19
> **forestpixie said:**
> If you remove splash then you will see the file check at the expense of seeing all of the boot procedure.

Can you explain which line from the /boot/menu.lst file I need to amend to remove splash.

---

### Post by Elfy on 2008-12-19
Once you have the file opened for editing, might be good to back it up first with

```
sudo cp /boot/grub/menu.lst
```

You will be presented with a whole load of various text lines - page down until you reach ## ## End Default Options ##

Now you are looking at the actual lines which appear on your menu list - look at the first stanza and then the kernel line -  mine looks like

```
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=9d44e64b-0c3f-4376-93f5-7e0a4bc9afac ro quiet splash 
```

You can see splash and quiet at the end of the line - you need to remove quiet, not splash I believe though, nothing to stop you removing both.

Save and on reboot it should be noisy.

Once you have decided that is what you need/want then open the file for editing again and find the line near the beginning which says - # defoptions=quiet splash - this line tells update grub to add quiet and splash to the boot option - add a # to the beginning of the line and it will stop that.

---

### Post by heyup on 2008-12-19
> **forestpixie said:**
> 

You will be presented with a whole load of various text lines - page down until you reach ## ## End Default Options ##

Now you are looking at the actual lines which appear on your menu list - look at the first stanza and then the kernel line -  mine looks like

```
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=9d44e64b-0c3f-4376-93f5-7e0a4bc9afac ro quiet splash 
```

You can see splash and quiet at the end of the line - you need to remove quiet, not splash I believe though, nothing to stop you removing both.

Save and on reboot it should be noisy.

That is exactly what I did yesterday. I removed 'quiet' from that line and saved the menu.lst file. When I rebooted, the result was some text flashes past before the file system check starts (as tiny unreadable text) with the normal image of a horizontal bar moving sideways across back and forth.

The file system check doesn't seem to become visible.

---

### Post by Elfy on 2008-12-19
Post your menu list then, let us have a look. Please put [noparse]```
[/noparse] at the beginning of the paste and then put [noparse]
```[/noparse] at the end.

It might be the splash resolution - possibly, have you tried with splash removed from the line?

Just so you are aware, there is a GUI app which will give you the same options if you prefer - startup manager - [http://ubuntuforums.org/showpost.php?p=5112620&postcount=1](http://ubuntuforums.org/showpost.php?p=5112620&postcount=1)

---

### Post by heyup on 2008-12-19
I removed 'quiet splash' from kernel line in the menu.lst and that seems to be the answer (I'll have to wait until the next file system check to be sure). I removed 'quiet' last time I tried.

Thanks for your help and the link - which is very useful to know.

---

