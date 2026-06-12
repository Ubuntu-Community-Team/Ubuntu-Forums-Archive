---
title: "What is meaning of &quot;#!/bin/bash&quot;?"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Fanatico on 2010-09-09
Each script file starts begin with #!/bin/bash line.

Can anyone explain what is exact meaning of this line?

Do I understand correctly, that this line means starting new instance of shell process to execute this specific script file and then exit?

Thanks

---

### Post by snkiz on 2010-09-09
Tell the shell what type of shell your using, It could be #!/bin/py or bin/sh or any number of others.

---

### Post by Fanatico on 2010-09-09
Thank you for your response.

If this line doesn't mean starting new shell process, then I don't understand how one can use shell script for /init process in initramfs?

Please see section Init in  [http://en.gentoo-wiki.com/wiki/Initramfs](http://en.gentoo-wiki.com/wiki/Initramfs)

[B]Init

The file structure of your initramfs is almost complete. The only thing that is missing is /init, the executable in the root of the initramfs that is executed by the kernel once it is loaded. Because sys-apps/busybox includes a fully functional shell this means you can write your /init binary as a simple shell script (instead of making it a complicated application written in Assembler or C that you have to compile).[/B]

---

### Post by undecim on 2010-09-09
That specifies what program should interpret the script.

If you double-click on a script file, that first line determines what program is launched with that script fed to it. So if it's a python script, you would have #!/usr/bin/python2.6 or something like that. In that case, it's particularly useful to ensure that the correct version of python is being used on the script.

I believe that #! is called a "crunchbang"

---

### Post by slakkie on 2010-09-09
> **undecim said:**
> 
I believe that #! is called a "crunchbang"

Also called hashbang, it has many names :)

---

### Post by Fanatico on 2010-09-09
> **undecim said:**
> That specifies what program should interpret the script.

If you double-click on a script file, that first line determines what program is launched with that script fed to it.

Thank you for your response.

OK, now I understand that "crunchbang" causes to start shell process in init script and then perform script commands.

---

### Post by egalvan on 2010-09-09
google  #!/bin/bash linux **shebang**
gives


[http://en.wikipedia.org/wiki/Shebang_%28Unix%29](http://en.wikipedia.org/wiki/Shebang_%28Unix%29)


this page has a lot of information; good reading if you REALY want to understand.

---

