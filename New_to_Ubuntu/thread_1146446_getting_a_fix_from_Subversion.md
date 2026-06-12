---
title: "getting a fix from Subversion"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-05-02
Hello,
There appears to be a fix for a program that I use. The fix was placed in Subversion. I've just installed subversion. But how do I go about getting that fix for the program.

Please see [https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/300240/comments/4](https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/300240/comments/4)

---

### Post by MrWES on 2009-05-02
> **hanzj said:**
> Hello,
There appears to be a fix for a program that I use. The fix was placed in Subversion. I've just installed subversion. But how do I go about getting that fix for the program.

Please see [https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/300240/comments/4](https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/300240/comments/4)

I'm assuming you still have the program trunk from the original install. If so, cd into the /trunk/<programname> and issue a 
```
svn up
``` command. Then autogen.sh | configure | make | make install.

Or check out checkinstall

[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

Bill

[http://svnbook.red-bean.com/en/1.0/svn-book.html]("http://svnbook.red-bean.com/en/1.0/svn-book.html")
[http://sourceforge.net/scm/?type=svn&group_id=67873]("http://sourceforge.net/scm/?type=svn&group_id=67873")

---

### Post by hanzj on 2009-05-02
You wrote: "I'm assuming you still have the program trunk from the original install."

My gtkpod program was installed from the official/regular ubuntu repository. 

Are we talking about the same thing?

---

### Post by MrWES on 2009-05-03
> **hanzj said:**
> You wrote: "I'm assuming you still have the program trunk from the original install."

My gtkpod program was installed from the official/regular ubuntu repository. 

Are we talking about the same thing?

goto the second link I posted; it contains the svn source package for gtkpod.

Bill

---

### Post by hanzj on 2009-05-04
I checked out your second link:


> ```
svn co https://gtkpod.svn.sourceforge.net/svnroot/gtkpod gtkpod         	              
```         	[B]Warning
This is a generic Subversion checkout command which will pull all modules, tags and/or branches of the project. Please refer to project home page for specific SVN instructions, or use "Browse Repository" link; in most cases, you will want to add '/trunk' to the HTTPS URL above to check out only trunk (main development line).[/B]



Where do insert "/trunk"? And is inserting "/trunk" what I want to do?

---

