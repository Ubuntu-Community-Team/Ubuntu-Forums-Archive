---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by now0pen on 2011-03-03
I was trying to install wine following this--

**4) Wine**

Wine is a must-have application for those who can’t  live without their Windows applications, It allows you to install your  Windows application in your Ubuntu machine and run them like native  Windows apps.
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] [COLOR=#c20cb9]**wine**[/COLOR]

Once you have installed Wine, remember to run the configuration (*Applications -> Wine -> Configure Wine*) before attempting to install your favorite Windows app.


source: [http://mcaf.ee/0c243](http://mcaf.ee/0c243)


Terminal came up with EULA. I did not know how to proceed. I pressed enter, typed OK then enter and nothing happened. I decided to close terminal. 



When I opened terminal again and ran another "sudo apt-get install" this was what I got:


"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "

I restarted my pc and still got the same message on my terminal.

I typed  'sudo dpkg --configure -a'" but nothing happened.

What did I just do here and what happened? What should I do now?

It's my first week on ubuntu. Thanks!

---

### Post by lisati on 2011-03-03
If you got no output from the dpkg --reconfigure command, it probably worked. It's safe to try your next installation again. Feel free to let us know how you get on.

---

### Post by now0pen on 2011-03-03
I think things are working now. I was able to open the wine configuration window. Thanks!

---

### Post by now0pen on 2011-03-03
mark this thread as solved?

---

### Post by sandyd on 2011-03-03
> **now0pen said:**
> I was trying to install wine following this--

**4) Wine**

Wine is a must-have application for those who can’t  live without their Windows applications, It allows you to install your  Windows application in your Ubuntu machine and run them like native  Windows apps.
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] [COLOR=#c20cb9]**wine**[/COLOR]

Once you have installed Wine, remember to run the configuration (*Applications -> Wine -> Configure Wine*) before attempting to install your favorite Windows app.


source: [http://mcaf.ee/0c243](http://mcaf.ee/0c243)


Terminal came up with EULA. I did not know how to proceed. I pressed enter, typed OK then enter and nothing happened. I decided to close terminal. 



When I opened terminal again and ran another "sudo apt-get install" this was what I got:


"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "

I restarted my pc and still got the same message on my terminal.

I typed  'sudo dpkg --configure -a'" but nothing happened.

What did I just do here and what happened? What should I do now?

It's my first week on ubuntu. Thanks!
^do this

then when installing again, and doing EULA, press [TAB]

---

### Post by now0pen on 2011-03-03
Thanks for that EULA tip. I'll do that next time.

Wine is now downloading .NET to my pc. I think everything is running as it should. I'll mark this thread as solved then.

I appreciate your help. Thank you very much!

---

