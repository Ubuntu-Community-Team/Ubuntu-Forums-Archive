---
title: "flash player kubuntu-restricted-extras"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by gshockxc on 2009-04-09
I did a search for similar issues, and found this post where the problem has been solved, [http://ubuntuforums.org/showthread.php?t=982597&highlight=flash+video+player](http://ubuntuforums.org/showthread.php?t=982597&highlight=flash+video+player)

So I followed the same instructions, from the Terminal I typed:
 sudo apt-get install kubuntu-restricted-extras

And this is what I got:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any thoughts?  Thanks.

---

### Post by Ayuthia on 2009-04-09
This message usually means that something like Synaptic/Adept or a system update (via apt-get update/upgrade) might be running at the time.  If that is the case, just close Synaptic or wait until the update is complete and then you should be able to run the command.

---

### Post by gshockxc on 2009-04-10
I think I did have another package manager running at the time.  Thanks, I'll try this again.  

*Edit:* Tried.  Worked.  Thanks.

How do you mark thread as [Solved]?

---

### Post by Jakey_TheSnake on 2009-04-10
It's in "Thread Options" at the top.

---

### Post by gshockxc on 2009-04-10
> **Jakey_TheSnake said:**
> It's in "Thread Options" at the top.

Not to be 'dim' but I'm not seeing it.  I see 'Thread Tools,' but there's nothing under that option.  I'm using Firefox, but I can't imagine that it would display differently.  I remember using it before, but it's been months since I've posted.  I apologize, I'm just not seeing it...

**Thread Tools | Search this Thread | Display Modes**

I don't see any options for 'Mark thread as [Solved]'

---

### Post by Paqman on 2009-04-10
I think they got rid of that feature a little while ago. It did use to be there.

---

### Post by gshockxc on 2009-04-10
> **Paqman said:**
> I think they got rid of that feature a little while ago. It did use to be there.

Thank you for saying that.  I was beginning to think that I was losing my mind.  I still might be, but at least it will be for other reasons.  

Thanks for the help.

---

