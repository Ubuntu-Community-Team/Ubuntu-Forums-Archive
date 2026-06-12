---
title: "how to install a driver?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by macaklinka on 2009-12-15
Hi all who are willing to help!

I am comletely new to Ubuntu, just installed it. I can't get my analog TV card to work :(

There is a [driver]("http://www.avermedia.com/avertv/Support/DownloadCount.aspx?FDFId=3216") on the official card's site (AVerMedia), but I don't know how to install. There are some instructions that came with it, but I don't quite get them. 

They say: "Launch command terminal
2. Act as root to install driver. There are two ways to do this.

  (1) Use sudo. Recommended for Ubuntu Linux users. You need to type your own
      password:

      $ sudo ./AVERMEDIA-Linux-x86-H826D-0.10-beta.sh
      Password:"Type your password here"

  (2) Use su. Recommended for most users. You need to type root password:

      $ su
      Password:"Type root password here"
      # ./AVERMEDIA-Linux-x86-H826D-0.10-beta.sh"

Now I tried copy-pasting these into the terminal, but it replies: "Command not found". Obviously I'm missing something here.

Please help if you have some insight!

Thanks!

---

### Post by Physical Hook on 2009-12-15
Let's assume you extracted the .zip file in your home directory ( /home/user ):

```

cd $HOME/AVERMEDIA/
sudo ./AVERMEDIA-Linux-x86-H826D-0.10-beta.sh
```** $HOME/AVERMEDIA is just an example - change the directory name to the one which were created when you extracted the .zip file.

If the command not found error still persists, please copy and paste the Terminal output along with the .sh file contents ( use [code] tags ).

---

### Post by macaklinka on 2009-12-15
Thank you :)

Managed to install the driver!

---

