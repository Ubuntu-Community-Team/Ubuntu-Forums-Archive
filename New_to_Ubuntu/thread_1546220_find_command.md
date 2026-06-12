---
title: "find command"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by bigsigh on 2010-08-05
I've been unable to figure out how to stop the screen output from overrunning.

The find results are at the top of the return list, I can see them for a split second as they scroll past, but the rest of the useless results run the needed results out.

I'm trying to find all files with fetchmail in the title.

I can't figure out how to integrate the more command or anything to control the screen output.

I've read page after page after page after page after page of google results and none of them discuss controlling the screen output with a command like more.

example: find \ -name 'fetchmail*' -exec more \;
does not work to control the output.

This seems like such a simple thing to me, yet try as I might I'm unable to find the correct command syntax.

Why is Linux cli so damned frustrating for such simple results??????????

Why do the Linux developers not understand that Linux will never supplant microsoft until they can simplify basic command structure manuals.


GD this is so time consuming and frustrating.

---

### Post by bigsigh on 2010-08-05
I've been unable to figure out how to stop the screen output from overrunning.

The find results are at the top of the return list, I can see them for a split second as they scroll past, but the rest of the useless results run the needed results out.

I'm trying to find all files with fetchmail in the title.

I can't figure out how to integrate the more command or anything to control the screen output.

I've read page after page after page after page after page of google results and none of them discuss controlling the screen output with a command like more.

example: find \ -name 'fetchmail*' -exec more \;
does not work to control the output.

This seems like such a simple thing to me, yet try as I might I'm unable to find the correct command syntax.

Why is Linux cli so damned frustrating for such simple results??????????

Why do the Linux developers not understand that Linux will never supplant microsoft until they can simplify basic command structure manuals.


GD this is so time consuming and frustrating.

---

### Post by oldos2er on 2010-08-05
```
<command> | more
``` or ```
<command> | less
``` whichever you prefer.

---

### Post by hudsonl on 2010-08-05
> **bigsigh said:**
> I've been unable to figure out how to stop the screen output from overrunning.

The find results are at the top of the return list, I can see them for a split second as they scroll past, but the rest of the useless results run the needed results out.

I'm trying to find all files with fetchmail in the title.

I can't figure out how to integrate the more command or anything to control the screen output.

I've read page after page after page after page after page of google results and none of them discuss controlling the screen output with a command like more.

example: find \ -name 'fetchmail*' -exec more \;
does not work to control the output.

This seems like such a simple thing to me, yet try as I might I'm unable to find the correct command syntax.

Why is Linux cli so damned frustrating for such simple results??????????

Why do the Linux developers not understand that Linux will never supplant microsoft until they can simplify basic command structure manuals.


GD this is so time consuming and frustrating.

find <startingPath> -name '*fetchmail*' -print  | more

> find / -name '*fetchmail*' -print | more

OR ... start at a different directory ...

> find /var -name '*fetchmail*' -print | more

OR  may need to run as root ...

> sudo find / -name '*fetchmail*' -print | more

OR ... if you want to see file permissions ...

> sudo find / -name '*fetchmail*' -exec ls -l {} \; | more

OR ... if you want to search case-insensitive (**iname**) and see file permissions ...

> sudo find / -**iname** '*fetchmail*' -exec ls -l {} \; | more

---

### Post by cariboo on 2010-08-05
Merged two threads that were probably caused by database problems.

---

### Post by bigsigh on 2010-08-05
> **cariboo907 said:**
> Merged two threads that were probably caused by database problems.

Indeed, struggling with a simple command and the forums weren't working to boot, nothing like compounding existing frustration.

I wasn't using sudo.

sudo find / -name 'fetch*' | more

works just fine as sudo

who da thunk one would need sudo for a file system search?

Pissed away yet another evening of my life on computers for no good return.

Sigh.

---

