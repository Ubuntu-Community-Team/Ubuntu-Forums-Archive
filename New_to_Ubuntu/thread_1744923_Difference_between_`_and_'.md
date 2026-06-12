---
title: "Difference between ` and ' ?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Iecur on 2011-04-30
Okay well I guess it's about time I got around to asking about this.  I know I should be ashamed of myself for not knowing this.  I've actually been meaning to ask this for months but I've been so ashamed that I haven't bothered doing anything whatsoever with Linux I've actually gone back to Windows and living carefree forgetting everything that I had learned about Linux up till now.  Rather than get scolded for not knowing something so obvious.

Well, yeah let's get to business I ran into a script for backing up files.  Here it is:
```
#!/bin/bash
# make copies of all files in a directory
LIST=`ls`
for i in $LIST; do
	ORIG=$i
	DEST=$i.old
	cp $ORIG $DEST
	echo "copied $i"
done
```

And well I figured I won't really learn if I just copy and paste.
So I typed it out but like so:
```
#!/bin/bash
# make copies of all files in a directory
LIST='ls'
for i in $LIST; do
	ORIG=$i
	DEST=$i.old
	cp $ORIG $DEST
	echo "copied $i"
done
```

Ran chmod 700 or whatever you do I can't believe I've forgotten so much already.  And it didn't work.  I just figured the script didn't work.  I was was thinking maybe that doesn't work on the later versions of Linux or Ubuntu or whatnot. So, I didn't think much about it anymore.  Then I ran into it again and I figured what if I just copy and paste it ?  So I did.  And when I ran it it worked. So that just confused the hell out of me. Especially since I think in gedit they (` and ') are even different colours I think.  Not sure which I'm sort of colour blind.  In most articles I ran into talking about writing scripts/working on terminal whatnot just says use single quotes for this or that.  And I've been using ' ' for quite some time and it always seemed to work fine for everything else that I did.  And it seems that I can't use ` in place of ' but I'm sure everyone already knew that..
I ran into this: [http://www.cs.sfu.ca/~ggbaker/reference/characters/](http://www.cs.sfu.ca/~ggbaker/reference/characters/)
But it didn't really talk about their uses other than don't use one for the other which I see is true here too.  And confusing since the backtick which is what ` is right ?  Seems to be called the grave accent but there is another key called the grave accent ?  As the little old ladies would say here, "Voi voi voi."

So right if anyone could help me out and tell me what each one's specific job is or maybe a link to something explaining it I would greatly appreciate it.  And sorry for having to ask this.  At least I'm in the right part of the forums. x'D

---

### Post by 5149.5 on 2011-04-30
This[ link]("http://goo.gl/tMxm8") should help.

---

### Post by Lateralis on 2011-04-30
Anything inside a backtick is assumed to be a command and is executed.  In this specific case, the output of `ls` is saved in LIST.  In the second case, ls in normal quotes is not executed as a command, so LIST doesn't contain a list of files but only 'ls'.  

Also, really, don't be worried about asking questions!  If you have one, ask one!  No one here will judge you if you asked a question you felt was "stupid." =)

---

### Post by hakermania on 2011-04-30
Also, instead of `command` please use the more modern $(command)   :D

---

### Post by migs73 on 2011-04-30
**To ask is but a moments shame, not to ask and to remain ignorant, is a lifelong shame.** Ancient Chinese proverb (?).

I might add that to my sig.

---

