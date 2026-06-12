---
title: "mv command deletes file"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by ras84 on 2011-08-22
When I'm trying to move a file to new location the file disappears.

```

ras@ras-Vostro-1015:~/Desktop$ ls -a
.  ..  randomfile.txt
ras@ras-Vostro-1015:~/Desktop$ sudo mv randomfile.txt /Documents 
ras@ras-Vostro-1015:~/Desktop$ cd
ras@ras-Vostro-1015:~$ cd Documents/
ras@ras-Vostro-1015:~/Documents$ ls -a
.  ..
ras@ras-Vostro-1015:~/Documents$ 


```the file is not in Desktop, Documents or in Trash:confused:

---

### Post by dave01945 on 2011-08-22
by the looks of it your moving it to /Document not ~/Documents also the sudo command might be moving it to /root/Documents if they are your files you don't need to use sudo

--edit--

just tried your command and it did move it to /Documents not /home/user/Documents

the file is in the root filesystem

---

### Post by ras84 on 2011-08-22
can't use mv command without sudo...

```

ras@ras-Vostro-1015:~/Desktop$ ls
randomfile.txt
ras@ras-Vostro-1015:~/Desktop$ mv randomfile.txt /Documents
mv: cannot move `randomfile.txt' to `/Documents': Permission denied
ras@ras-Vostro-1015:~/Desktop$ 



```

---

### Post by Wim Sturkenboom on 2011-08-22
> **ras84 said:**
> When I'm trying to move a file to new location the file disappears.

```

ras@ras-Vostro-1015:~/Desktop$ ls -a
.  ..  randomfile.txt
ras@ras-Vostro-1015:~/Desktop$ sudo mv randomfile.txt /Documents 
ras@ras-Vostro-1015:~/Desktop$ cd
ras@ras-Vostro-1015:~$ cd Documents/
ras@ras-Vostro-1015:~/Documents$ ls -a
.  ..
ras@ras-Vostro-1015:~/Documents$ 


```the file is not in Desktop, Documents or in Trash:confused:

/Documents and /home/yourusername/Documents are two different things. Unless you have a directory /Documents, I'm not surprised that you needed to use sudo.

---

### Post by dave01945 on 2011-08-22
your still writing it wrong /Documents isn't your documents / indicates the root filesystem try this

```
mv randofile.txt ~/Documents 
```

this will work

also if you type 

```
 cd /
ls 
```

you will see a new Documents folder with the file you previously moved in it but because you done it with sudo you will need sudo to get in to that folder

---

### Post by Wim Sturkenboom on 2011-08-22
> **ras84 said:**
> can't use mv command without sudo...

```

ras@ras-Vostro-1015:~/Desktop$ ls
randomfile.txt
ras@ras-Vostro-1015:~/Desktop$ mv randomfile.txt /Documents
mv: cannot move `randomfile.txt' to `/Documents': Permission denied
ras@ras-Vostro-1015:~/Desktop$ 

```
Of course not; normal users don't have permission to write in the root directory '/'.

---

### Post by nothingspecial on 2011-08-22
> **dave01945 said:**
>  

```
 cd /
ls 
```

you will see a new Documents folder with the file you previously moved in it 

Actually randomfile.txt will have had it's name changed to Documents and will be in /

mv does not create directories but it will rename the file if the destination doesn't exist.

---

### Post by ras84 on 2011-08-22
tnx, i generally understand now, 
```
ras@ras-Vostro-1015:~/Desktop$ mv randomfile.txt /home/ras/Documents/ 
```had been the right (easy-to-undertand-to-n00b) code

---

### Post by bodhi.zazen on 2011-08-22
"/home/ras" can be abbreviated by ~

Assuming you are in ~ already, you can use Documents rather then /Documents

See relative vs absolute path.

relative = relative to your current directory

absolute = starting with /

---

