---
title: "transfer files over ssh"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Sceiron on 2010-02-11
Is it possible to transfer files over ssh using putty?

I want to download files from my ubuntu computer at home, using a laptop running win xp. I usually log in to my ubuntu machine on ssh using putty.

Can i transfer files over ssh using putty? If so, how do i do it?

What are the alternatives for this kind of filetransfer?
FTP is kinda obvious, is there any other?

Thanks
Sceiron

---

### Post by wobin77 on 2010-02-11
Maybe this helps setting up putty?

[http://www.electrictoolbox.com/article/applications/ssh-putty/](http://www.electrictoolbox.com/article/applications/ssh-putty/)

---

### Post by aeiah on 2010-02-11
on windows you'd use pscp (linux uses scp). pscp should be bundled with putty. its command line and works the same way as the linux scp (pscp is putty's secure copy)

you may find it easier however to use winscp. it's gui, and behaves just like an ftp client.

if you're automating backup and whatnot, you'd want to control pscp from within a .bat file in windows i guess. anyway, the syntax for pscp and scp is:
```

pscp copythis tohere

```

eg to copy test.txt from windows to your linux desktop you'd open a windows command prompt and do:
```

pscp c:\path\to\test.txt user@my-ubuntu-machine:/home/user/Desktop/test.txt

```

likewise, to pull things from ubuntu you'd do:
```

pscp user@my-ubuntu-machine:/home/user/Desktop/test.txt test.txt

```

if you use a different port for ssh than the default you'd add -P number after pscp. the same goes for using it under linux, except its scp not pscp.

---

### Post by Sceiron on 2010-02-11
> **aeiah said:**
> 
likewise, to pull things from ubuntu you'd do:
```

pscp user@my-ubuntu-machine:/home/user/Desktop/test.txt test.txt

```

if you use a different port for ssh than the default you'd add -P number after pscp. the same goes for using it under linux, except its scp not pscp.

I belive this is excatly what i'm looking for. Had to install putty tools for it to use the pscp command. However, when i performed the above command the file ended up in my /home directory on the remote machine (Ubuntu). How to i transfer it to my client(xp), do i have to specify localhost somehow?

---

### Post by bartonski on 2010-02-11
This also depends some on how you're copying files. If you're copying a deep directory structure, you might want to something like this:

```
tar zcvf - ./deep_directory | ssh user@remote.machine tar zxvf -

```
This approach also has an advantage when you're trying to copy files to a machine that you can't directly access (on the other side of a firewall, for instance):

```
tar zcvf - ./deep_directory | ssh -t user@border.machine ssh user@behind.firewall tar zxvf -
```

Note: I haven't tested the second of these, it might need a little tweaking.

---

