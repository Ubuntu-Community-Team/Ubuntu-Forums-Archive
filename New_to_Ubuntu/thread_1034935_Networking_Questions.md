---
title: "Networking Questions"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Cheemag on 2009-01-09
Using Places | Network in the GUI:
Double-clicking on a shared directory on an XP box
networked to the Linux machine calls for a password.

My Linux password is input and [Connect] is pressed - it
comes back again and again for the password. Pressing
'Remember forever' does not work, nor does any
'Remember' option for that matter.

However, if I try this just after booting, everything
goes as it should and I can access my Windows shared dirs.
If 'Remember forever' is selected, it seems that that
particular XP directory is accessible thereafter.

And on the other hand some Windows directories are
accessible without a password and others aren't.
All the Windows directories are fully shared network/
read/write.

There is no problem accessing Linux shared dirs on the
Windows box.

Subsidiary question: how can I prevent Ubuntu mounting
the directories I can share on the desktop?

---

### Post by cmnorton on 2009-01-09
This sounds like you need to run smbpasswd on the Linux side. You would be establishing the smb user and password that matches who is logging in.

---

### Post by superprash2003 on 2009-01-09
use advanced file sharing in windows.. and enter windows username and password.. not ubuntu.. [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx)

---

### Post by Cheemag on 2009-01-10
> **superprash2003 said:**
> use advanced file sharing in windows.. and enter windows username and password.. not ubuntu.. [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx)

As far as I know I require no usernames and passwords in
Windows. I don't even have to sign on to XP - I am the only
user!

All the XP shared folders are read/write.

I have two XP machines which network seamlessly without the need
of passwords, the Linux machine has now joined them, but there
CAN be difficulties accessing one of the machines from Linux.
I can access all the shares on the second machine.



The problem is still there - I can access some XP folders but
not others, and now I cannot access the ones I was able to
access yesterday without any password being demanded.

I ran smbpasswd and gave it a new password, but the problem
persists.

---

### Post by Kellemora on 2009-01-10
Hi Cheemag

You should have just hit ENTER with no password if a windows box asked for one.

By clicking on REMEMBER PASSWORD, if you typed a password in, that password is now stored and autofills and possibly now bypasses the password screen completely.

IF you can get the password screen up, delete the password and then hit REMEMBER PASSWORD to store the blank password, if it will let you.

I've made this mistake myself a few times, since I have a mix of Ubuntu and Windows boxes on my system.  To fix it I would have to delete my user password and set a new one.  Then the next time I tried to access a windows box, SAVE the blank password.  Then go back and reset my user password back to what it was before I made the goof.  You have to go into root to fix passwords by the way.

TTUL
Gary

---

### Post by Cheemag on 2009-01-11
> **Kellemora said:**
> Hi Cheemag

You should have just hit ENTER with no password if a windows box asked for one.

By clicking on REMEMBER PASSWORD, if you typed a password in, that password is now stored and autofills and possibly now bypasses the password screen completely.

IF you can get the password screen up, delete the password and then hit REMEMBER PASSWORD to store the blank password, if it will let you.

I've made this mistake myself a few times, since I have a mix of Ubuntu and Windows boxes on my system.  To fix it I would have to delete my user password and set a new one.  Then the next time I tried to access a windows box, SAVE the blank password.  Then go back and reset my user password back to what it was before I made the goof.  You have to go into root to fix passwords by the way.

TTUL
Gary

I've changed the password using smbpasswd, but it makes no
difference.

How does one "save" the blank password?

Go into root?

I'm quite new to this Linux stuff - I find doing even the
simplest tasks extremely involved.

---

### Post by Kellemora on 2009-01-11
Hi Chee

The password, if you were trying to access a windows box and it is what asked for your password, then it will be on the windows box somewhere.

I probably can't help you beyond this point as Windows has so many flavors and none of them seem to work the same or store things in the same places.  And it was quite a while ago when I fixed them so they wouldn't ask for a password.  I only have XP-Pro and XP-MCE left here.  XP-MCE has got to be the worst flavor of XP Mickey$oft ever came out with!  Virtually nothing works right on it!  Probably why they abandoned it so quickly.  They are only used now to run some POS hardware and that's it.
As soon as I replace that hardware, they will be GONE too!

What is your password on your Windows machines?  Don't tell me, just try that password to see if it works.  If not, go into Windows Password Manager and see if you can delete Remembered Passwords from there.  That may only be and XP-Pro function or it may be because I had .net framework on the Pro machines too.

If you can't tell, I'm trying to FORGET I ever knew the Doze, hi hi........  Also, I'm olde and learning all this newfangled computin' contraption stuff uses 110% of what brain cells I have left, hi hi......

Good Luck on figuring it out!

TTUL
Gary

---

