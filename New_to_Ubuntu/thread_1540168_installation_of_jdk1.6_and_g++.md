---
title: "installation of jdk1.6 and g++"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by manish411 on 2010-07-27
[SIZE=3]hi ! I am a beginner and installed ubuntu 10.04 yesterday.
I need to install jdk and g++ so that i can run programs .
plz guide me
[/SIZE]

---

### Post by ThesaurusRex on 2010-07-27
Go to Applications->Ubuntu Software Center. Then just run searches for what you want.

---

### Post by Souptik on 2010-07-27
> **manish411 said:**
> [SIZE=3]hi ! I am a beginner and installed ubuntu 10.04 yesterday.
I need to install jdk and g++ so that i can run programs .
plz guide me
[/SIZE]
Here's how you install jdk 1.6.
1. Download <file_name>.bin from [www.sun.com](www.sun.com) (not java.com as then you will get the jre not the jdk)
2. Store it to the home folder.
3. Go to Applications-->Accessories-->Terminal
4.type "chmod a+x <name_of_file>.bin"
5. type "sudo <name_of_file>.bin"
6.enter your password. Note the password will not appear on screen to protect your password.
7.The license agreement appears.
8.press the space bar to flip through the license.
9.At "do you agree to license terms(y/n)? " press y
10.jdk installed.
Please take care of your punctuation.:KS

---

### Post by anewguy on 2010-07-27
You can load G++ right from Synaptic Package Manager, but a better step would be to install the build-essential package in Synaptic Package Manager.

Dave

---

