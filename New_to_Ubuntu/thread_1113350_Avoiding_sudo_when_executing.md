---
title: "Avoiding sudo when executing"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by TideMan on 2009-04-01
I've installed a program in /usr/share and I want to execute it from my home directory, but can only do so if I use sudo and enter my password.

Here are the permissions of the executable:
```
-rwxr-xr-x 1 root root 58971 2009-04-01 22:25 matlab
```

I understood those x's meant that it could be executed by anyone from anywhere.

Obviously, I've got it wrong.
So how can I avoid having to use sudo?

BTW, the background to this forum has tuned a ghastly shade of green/yellow. Is this happening for anyone else?

---

### Post by ibuclaw on 2009-04-01
Where is the location of the matlab executable?
```
which matlab
```
```
whereis matlab
```

It should be located, or linked in one of these directories:
[LIST]
[*]**/usr/bin**
[*]**/usr/local/bin**
[/LIST]

Regards
Iain

---

### Post by stchman on 2009-04-01
> **TideMan said:**
> I've installed a program in /usr/share and I want to execute it from my home directory, but can only do so if I use sudo and enter my password.

Here are the permissions of the executable:
```
-rwxr-xr-x 1 root root 58971 2009-04-01 22:25 matlab
```

I understood those x's meant that it could be executed by anyone from anywhere.

Obviously, I've got it wrong.
So how can I avoid having to use sudo?

BTW, the background to this forum has tuned a ghastly shade of green/yellow. Is this happening for anyone else?

Yes these are the April Fools colors.

The thing to do is to make the permissions 755 on Matlab when owned by root.

---

### Post by TideMan on 2009-04-01
I'm sorry I've wasted people's time.
The problem was with the Matlab license manager, which I've now solved.

For anyone who has a similar problem with installing Matlab, you need to edit MLM.opt in $MATLAB/etc to reflect your user name, not root.  Then you need to reload the license manager using lmstart (in the same directory).

April Fools' colours are OK for 1-Apr, but in this hemisphere (longitude 174 deg E) it has been 2-Apr for 10 hours now.

---

