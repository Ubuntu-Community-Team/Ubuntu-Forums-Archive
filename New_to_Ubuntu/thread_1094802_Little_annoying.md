---
title: "Little annoying"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by jfalco on 2009-03-13
Hey all, 

New to Linux (about 2 weeks)! Tried OpenSUSE first the swithed to Ubuntu (Love It)!

Anyways, quick question. The little Trash icon in the lower right always show something in it and when I mouse over it says "1 item in trash" 

Open the trash and ain't nuttin there!! View>Show hidden files still nothing. Empty Trash doesn't work either.

No big deal, just a little annoying. Bug maybe? Any ideas??

Thanks and looking forward to participating in the community.

--joe

---

### Post by Moop on 2009-03-13
Type ```
gksudo nautilus
``` into a terminal, then your password and empty the trash from the window that opens.

---

### Post by jfalco on 2009-03-13
Ok tried that

The folder contents could not be displayed.
Sorry could not display all the contents of "trash" : Opperation not supported.

and the thinking pointer just keeps spinnin????

thanks for the quick response, anymore ideas???

//also it says 0 items in the bottom left....

---

### Post by Panzor on 2009-03-13
Open up a term and type:
```
$ls -la /home/<yourusername>/.local/share/Trash/files/
```
If you see things other than "." and ".." then that is what is occupying your trash. Get rid of it with "rm" and if that doesn't work, use root permissions with 'sudo' to remove it.

---

### Post by jfalco on 2009-03-13
Ok here is the output...

```
joe@joe-laptop:~$ ls -la /home/joe/.local/share/Trash/files/
total 8
drwx------ 2 joe joe 4096 2009-03-12 21:25 .
drwx------ 4 joe joe 4096 2009-03-11 00:05 ..
```

so all i see is "." and ".." but I'm still showing trash. Like I said this isn't a real big deal, guess I'm just being a little OCD. 

Anymore suggestions???

---

### Post by Panzor on 2009-03-13
I totally understand man. Half the fun of ubuntu is making your system as perfect as you know how to make it.

Anyway, I can guarantee that nothing is in your trash, so the error must be in gnome. That goes over my head, sorry :/. The first thing I would do is search for this error in google with vague terms with "gnome" tacked on the end. I would do this for you, but it goes against my principles :P. I like to see people learn.

---

### Post by jfalco on 2009-03-13
Thanks for the help. I'm trying to learn as much as possible. This Linux thing has got me hooked!!! I don't sleep anymore!!! Wife thinks I'm nuts (she loves vista) <-pretty sure she's nuts!! Thinkin about closing my construction company and going to school to learn how to program!!! Anyways off to Google to try to find something. I'll post back if I figure it out. Thanks again.

--joe

P.S.

reading your sig

> Don't forget to thank people using the thank button

where is that THANK button?? I know where it is on most forums but I don't see it here???

---

### Post by danrche on 2009-03-13
jfalco,

New to Ubuntu myself, but use Fedora at work. Try restarting your x server, "press Ctrl + Alt + Backspace" it'll bring you back to your login page and may clear up your trash problem. I'm no expert so you may just be logining in again with the same results but I figure it's worth a shot right?

---

### Post by jfalco on 2009-03-13
Gonna mark this as solved.. 

Restarted and it showed as empty. Deleted a file and showed full. Emptied and showed empty again. Weird.. must have just been hung up or something. 

Still looking for that "THANKS" button though.

Thanks guys

--joe

---

### Post by jfalco on 2009-03-13
OK How do your mark as SOLVED and where the heck is that THANKS button?????

--joe

bear with me I'll get it

---

### Post by Maverickprowls on 2009-03-14
I don't know if this is helpful, but the way I dealt with this little problem was to remove the actual Trash folder from ~/.local/Trash using ```
sudo rm -r ~/.local/Trash
``` and then search for the gnome trash-applet running using ```
ps -ef | grep trash
``` and kill the app called gvfsd-trash.

My trashcan was immediately cleared, and I can also report that the Trash folder was immediately re-created next time I used it.

---

### Post by mvalviar on 2009-03-14
> **jfalco said:**
> OK How do your mark as SOLVED and where the heck is that THANKS button?????

--joe

bear with me I'll get it

Thread tools to mark threads as [SOLVED] and give thanks has been disabled ;(

---

### Post by jfalco on 2009-03-14
I don't see solved in thread tools

---

