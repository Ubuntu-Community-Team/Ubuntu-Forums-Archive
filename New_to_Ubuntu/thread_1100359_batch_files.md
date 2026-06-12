---
title: "batch files"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by bcbotha on 2009-03-19
do batch files work and opperate in linux? if so how?

---

### Post by mcduck on 2009-03-19
Do you mean .bat files from Windows? No, they don't. They are just a bunch of Windows terminal commands in a text file.

If you really need to, you could try with Wine, but I doubt that you'd get any good results.

---

### Post by SeanHodges on 2009-03-19
Linux uses [shell scripts]("http://en.wikipedia.org/wiki/Shell_script") where Windows would use .bat scripts. If the batch file you want to use is fairly simple, the best approach is to re-write it as a shell script:

Learn how to write shell scripts (one of many tutorials on the Web): [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

A good reference when converting a Windows batch script to a shell script: [http://tldp.org/LDP/abs/html/dosbatch.html](http://tldp.org/LDP/abs/html/dosbatch.html)

If an existing Windows batch script is very large or complex, and you cannot justify rewriting the script (e.g. it's a one-off thing) - then you have the option of running it inside DOSbox: [http://www.dosbox.com/](http://www.dosbox.com/) (you can install it by [clicking here]("apt://dosbox")). 

This will emulate DOS inside Linux and has good compatibility with many batch scripts. I would personally recommend DOSBox over Wine, as Wine is more focused on running Windows applications in Linux rather than batch scripts, but I wouldn't rule it out.

Ultimately, if you want to write a new "batch script" in Linux, you actually want to write a shell script.

---

