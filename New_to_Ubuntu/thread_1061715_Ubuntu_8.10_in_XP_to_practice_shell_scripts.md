---
title: "Ubuntu 8.10 in XP to practice shell scripts"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by flytoravi on 2009-02-06
I am newbie here i have just installed ubuntu8.10 in my xp
as per the guidance given in digit magazine indian edition.
my main aim is to practice advanced shell scripts.
but when i try nested queries it shows command not found in bash.
even compress command ,gunzip..is not found in ubuntu.
Is it possible to learn Advanced shell scripts using ubuntu8.10......?:(

---

### Post by ubhi on 2009-02-06
hi,

if you want to practice shell script.
follow the below things.

1. create a shell file from vi editor or what else u like.

vi test.sh
echo 'hello world'
#then press esp key & type :wq


2. make this executable by following command.

chmod +x test.sh

3. Run this shell script

sh test.sh

done

---

### Post by flytoravi on 2009-02-06
Hi,

I want to know about whether i can practice advanced shell scripts which involved nested qurries, if then else type.....?
#ss1
#cmpressing files
ls -la > listoffiles
date
compress listoffiles
:wq

$./ss1
command not found .....?
even gunzip, are not working ..........?

---

### Post by hyper_ch on 2009-02-06
if you want to start shell scripts have a look here:  [http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by flytoravi on 2009-02-06
Dude i will paste the exact shell script what i am trying to learn..?
Why compress,gunzip is not in ubuntu ..........?

---

### Post by ubhi on 2009-02-06
in ubuntu 
gunzip used as gzip

try gzip....for your task

---

### Post by ubhi on 2009-02-06
& for compress you have to use ncompress in ubuntu

so type at terminal

sudo apt-get install ncompress


----

---

