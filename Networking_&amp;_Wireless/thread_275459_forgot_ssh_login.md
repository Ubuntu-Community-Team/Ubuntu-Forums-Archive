---
title: "forgot ssh login"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by josh on 2006-10-11
hello!

i have 2 machines which has ssh on them. i usually connect to the other machine from my machine in my lan using ssh -X -l username hostip after that it asks me for a password. i forgot that password. i can always create a new key but i dont want to touch the old key. i just want to recover the password. by the way that pc has no monitor, no keyboard or mouse its just always on coz that is where i save my old files. i just need to get the password remotely. how do i do that? do i brute-force the machine? and how do i brute-force it so that i can recover my same old password. will i break the machine if i brute-force it?

---

### Post by skymt on 2006-10-11
How secure is your forgotten password? If it's very weak (< 4 chars), brute-forcing is possible in a reasonable time. Unfortunately, SSH has protection against brute-forcing passwords, so it will take a very, very long time.

Just hook up some I/O (a keyboard and monitor) to the computer and fix it directly.

---

### Post by josh on 2006-10-11
just 4characters as far as i can remember. too much work to hook up a keyboard and a monitor. could you tell me how to do that bruteforce thing? will it break my file storage pc? thanks!

---

### Post by skymt on 2006-10-12
Don't worry, brute-forcing won't break anything. It just means trying every possible password until one works. I haven't found any good SSH brute-force scripts on a brief Google, so I'm writing one. Expect it by tomorrow. :)

---

### Post by skymt on 2006-10-12
Actually, expect it today! I've attached it.

* Save the attachment to your desktop
* Open a terminal
* Do this:```
cd ~/Desktop
tar -xzf sshforce.tar.gz
./sshforce targethostname targetusername
```I assume you remember your username. ;)

Please set me know whether it works!

---

### Post by skymt on 2006-10-12
Oh, I forget to mention something. You need to install putty-tools first (sudo aptitude install putty-tools).

---

### Post by skymt on 2006-10-12
Wouldn't you know it, there was a bug in the script. If you downloaded it already, download it again. I just fixed it. Sorry 'bout that. :oops:

---

### Post by josh on 2006-10-12
hey skymt! believe it or not, it worked! great! how did you learn to script? any recommendations? thanks alot!

---

### Post by c0rrupt3d_fate on 2006-10-12
wow, nice... the scirpt really worked to remotely brute force? I'm curious josh, how long did it take and props to skymt ;)

---

### Post by skymt on 2006-10-13
You're welcome! I'm glad it worked! :) 

I learned shell scripting just by reading shell scripts. However, if you'd like an easier way, [the Bash Pragramming Introduction](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) is very good. If you finish that and would like more, there's the [Advanced Bash Scripting Guide](http://tldp.org/LDP/abs/html/index.html), which is obviously more advanced.

---

