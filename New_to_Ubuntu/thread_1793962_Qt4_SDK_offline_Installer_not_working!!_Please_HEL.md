---
title: "Qt4 SDK offline Installer not working!! Please HELP!!"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by codeartist on 2011-06-30
I have downloaded Qt 4 SDK from qt.nokia.com

as per the instruction after downloading the offline installer version(.run file) 

typed the following commands:
$ chmod u+x Qt_SDK_Lin32_offline_v1_1_2_en.run 
$ ./Qt_SDK_Lin32_offline_v1_1_2_en.run

instead of starting installation. It shows this error:
bash: ./Qt_SDK_Lin32_offline_v1_1_2_en.run: Permission denied

after that I had tried using sudo do so. 
like this
$ chmod u+x Qt_SDK_Lin32_offline_v1_1_2_en.run
$ sudo ./Qt_SDK_Lin32_offline_v1_1_2_en.run

then it shows following error:
sudo: ./Qt_SDK_Lin32_offline_v1_1_2_en.run: command not found


What can I do to install it? Please help me :(

---

### Post by codeartist on 2011-06-30
68 views, 0 replies. Thanks for not helping me. I found answer to my own question :)

---

### Post by kiranmatrixlee on 2011-09-04
But I cannot find any answers .so please help me.Urgent..........................


i tried
chmod u+x Qt_SDK_Lin32_offline_v1_1_3_en.run
./Qt_SDK_Lin32_offline_v1_1_3_en.run


and also

Press CTRL+ALT+T
cd to the downloaded file.
mv Qt_SDK_Lin32_offline_v1_1_2_en.run ./Qt_SDK_Lin32_offline_v1_1_2_en.**bin**
sudo su
chmod x Qt_SDK_Lin32_offline_v1_1_2_en.bin
./Qt_SDK_Lin32_offline_v1_1_2_en.bin.

---

### Post by snip3r8 on 2011-09-04
Try typing : ```
sudo su
``` before running the other commands

---

