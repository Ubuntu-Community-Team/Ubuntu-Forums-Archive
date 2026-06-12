---
title: "help for readpst"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by crabclaw on 2009-03-13
The shop I was working at closed down, I managed to save my emails in a pst file. I downloaded readpst in synaptic but am not used to working in terminal. The pst file is in a folder called outlook on my desktop. The initial message from readpst is posted here.

[http://pastebin.com/d7f6c7235]("http://pastebin.com/d7f6c7235")

many thanks for any help.

Jonnymac

---

### Post by llamabr on 2009-03-13
I don't know readpst, or libpst:

[http://www.five-ten-sg.com/libpst/](http://www.five-ten-sg.com/libpst/)

well enough to answer this.  It looks like pst is a proprietary file compression, that can't be opened by eudora or thunderbird.

I know it's discouraged to read the manual for this tool, but play around with the options and flags until you get it to a format you like.

So, what format would you like?  And what do you intend to do with this information when you get it out?

---

### Post by crabclaw on 2009-03-13
I just want to be able to read the emails, who sent them &c. The problem is just that I don't fully understand terminal commands as I never use them so I'm not too sure what to type in!

thanks

J

---

### Post by mikechant on 2009-03-13
Looking at the message received from the readpst command, it appears you did not supply any parameters. It looks as if all you need to do in the terminal window is first change to the right directory (folder):

```
cd Desktop/outlook
```

then to extract the data:

```
readpst yourfilename.pst
```

(you'll need quotes around the filename if it contains spaces or special characters, and in the cd command you must use capital 'D' when typing 'Desktop' as Linux is fully case-sensitive)

Then it looks as if readpst will create some mbx files which I guess thunderbird etc. can import. type the following command to see what file/s it has created:
```
ls -l
```

If readpst doesn't produce the format you want, try looking at the info you put on pastebin - this lists the possible flags. If any of them sound helpful, then try running the readpst command with the flag or flags added before the filename. For example, if you wanted output in kmail format:
```
readpst -k yourfilename.pst
```

---

### Post by crabclaw on 2009-03-13
many thanks. Ended up all being pointless as the emails I wanted were not there for some reason.

J

---

