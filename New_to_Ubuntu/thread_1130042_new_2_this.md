---
title: "new 2 this"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by amenja on 2009-04-19
Hi family i am in need of help, how do i get pass the error that pops up when i try to install or run a program it say " run dpkg manually " or only one software management tool can run at one time please close the other applications ....first:)

---

### Post by ELD on 2009-04-19
That would usually happen if you are say tring to install a .deb package while having update manager, synaptic package manager, add/remove or another .deb installer is open.

Run 1 at a time buddy.

---

### Post by riseringseeker on 2009-04-19
> **amenja said:**
> Hi family i am in need of help, how do i get pass the error that pops up when i try to install or run a program it say " run dpkg manually " or only one software management tool can run at one time please close the other applications ....first:)

As to the first, if it pops up while you are trying to install a program or an update - I can't remember ever seeing it while trying to **run** a program, you will need to open a terminal (Applications->Accessories->Terminal) and copy and paste the following line, followed by enter:

```
sudo dpkg --configure -a
```

It will ask you for your password.  (I am assuming you have root - same as Administrator in windoze) - privileges.)  

If you have whatever way you were trying to install still open though, it will fail telling you you cannot have more than one package manager open at a time.  Simply close that - I will guess you are using Add/Remove - close that window, don't minimize it, close it, and then paste the command back into the terminal.

It sometimes may be confusing to sift through the search results here, but you should give it a try.  I had to do so to confirm the proper syntax for the above command and found it in less than a minute.

---

### Post by amenja on 2009-04-19
how can i do that i am completly confused

---

### Post by theozzlives on 2009-04-19
applications>accessories>terminal, then follow the above instructions

---

### Post by amenja on 2009-04-19
cool i followed the steps u gave and it said that i have no packeage named 'a'

---

### Post by riseringseeker on 2009-04-19
> **amenja said:**
> how can i do that i am completly confused

How can you do what?  Search the forums?  Fix the dkpg error message?  Close a installation program?  

Remember, the people on this forum want to help you, but you have to make your questions specific - none of us can read minds (yet).  :)

Taking a guess here.  Close every program except the browser you are reading this in.  Open a terminal window by moving the mouse to the upper left corner and clicking on "Applications".  In the drop down menu that comes up, choose "Accessories", from that menu choose "Terminal".

Now copy and past the command from my last reply and follow the instructions there.

If I guessed wrong as to what you are having trouble with, please try to be more specific in your question.

---

### Post by riseringseeker on 2009-04-19
> **amenja said:**
> cool i followed the steps u gave and it said that i have no packeage named 'a'

It should have just returned you to the prompt, no message at all.  Did you copy and paste, or try to type it in?  Use copy and paste if you tried to type it.  Typing a command can cause typos to creep in.  A lot of commands are very sensitive to spaces, for example, or it is often easy to see a lower case "L" as an "I" or a "1".

---

### Post by Iowan on 2009-04-19
> **riseringseeker said:**
> A lot of commands are very sensitive to spaces... Context would seem to indicate "-a" became either just "a" or "- a".
  Sage advice: > **riseringseeker said:**
> Use copy and paste if you tried to type it.

---

### Post by WatchingThePain on 2009-04-19
Is this program in Synaptic?.

---

