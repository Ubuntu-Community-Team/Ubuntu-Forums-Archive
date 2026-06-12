---
title: "how to install bin file"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by rameshmanly on 2010-12-25
i am a beginner in ubuntu, please help me to install jdk-6u23-linux-i586.bin file in ubuntu 10.10

---

### Post by I'mGeorge on 2010-12-25
open your terminal and use the following commands

```

cd /path_to_your_bin_file
chmod a+x jdk-6u23-linux-i586.bin
./jdk-6u23-linux-i586.bin

```

---

### Post by sffvba[e0rt on 2010-12-25
Would suggest trying to get and use deb files... will save you issues later... Except if you know what you are doing... and in that case you would not be asking what you are where your asking it :p

Merry day to you all ;)


404

---

### Post by rameshmanly on 2010-12-25
manly@manly-Not-Specified:~$ cd /home/manly/Downloads
manly@manly-Not-Specified:~/Downloads$ chmod a+x jdk-6u23-linux-i586.bin 
manly@manly-Not-Specified:~/Downloads$ ./jdk-6u23-linux-i586.bin 
./jdk-6u23-linux-i586.bin: line 1: syntax error near unexpected token `<'
./jdk-6u23-linux-i586.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

i got the above error

---

### Post by I'mGeorge on 2010-12-25
download it again from here using the x86 version and not the i586 'cause unless you have ubuntu x86_64 it might not support it [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) , and see how it goes. By the way you can install java using synaptic from your repositories.

---

### Post by sffvba[e0rt on 2010-12-25
Yes, I retract previous statement, as far as possible use the Software Center... then deb files specifically for the version of Ubuntu you are using... then deb files, then other things (if you are brave) :p


404

---

### Post by rameshmanly on 2010-12-25
manly@manly-Not-Specified:~$ cd Downloads
manly@manly-Not-Specified:~/Downloads$ chmod a+x j
jdk-6u23-linux-i586.bin     jre-6u23-linux-x64-rpm.bin
manly@manly-Not-Specified:~/Downloads$ chmod a+x j
jdk-6u23-linux-i586.bin     jre-6u23-linux-x64-rpm.bin
manly@manly-Not-Specified:~/Downloads$ chmod a+x jre-6u23-linux-x64-rpm.bin 
manly@manly-Not-Specified:~/Downloads$ ./jre-6u23-linux-x64-rpm.bin 
Unpacking...
Checksumming...
Extracting...
./install.sfx.3328: 1: ELF: not found
./install.sfx.3328: 2: Syntax error: ")" unexpected
 
Done.

what can i do

---

### Post by I'mGeorge on 2010-12-25
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by oldos2er on 2010-12-25
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by bludgard on 2010-12-28
> **oldos2er said:**
> [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Very easy to follow for a beginner.

Thank you.I have been struggling with this as well.

JAVA instructions are a little cryptic for me.

---

### Post by todayisgood on 2011-01-28
Accidentally posting.

---

### Post by sffvba[e0rt on 2011-01-28
> **todayisgood said:**
> Accidentally posting.

It happens to most men sooner or later ;)



404
(Sorry for the spam... been a long night shift...)

---

