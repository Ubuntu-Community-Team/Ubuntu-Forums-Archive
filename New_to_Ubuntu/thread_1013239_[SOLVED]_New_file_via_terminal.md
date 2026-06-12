---
title: "[SOLVED] New file via terminal"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-12-16
I am creating a shell script and would like to know how to make a new file in the script.

I considered using 
```
vi example.txt 
```

however that will open up vi which I dont mind as long as it closes as soon as it opens.

So anyone have any answers?

---

### Post by drs305 on 2008-12-16
This command creates a new file called *filename*:
```

touch */path/filename*

```

Run it with sudo if it's going somewhere other than a folder owned by you.

---

### Post by Izek on 2008-12-16
research the **cat** command.

---

### Post by Nxion on 2008-12-16
Touch is the easiest way to do it.

---

### Post by linuxguymarshall on 2008-12-16
Is touch a universal Linux (UNIX) command. I want this script to work on ALL Linux systems.

---

### Post by run1206 on 2008-12-16
> **Nxion said:**
> Touch is the easiest way to do it.

agreed, i use touch as well.

---

### Post by jpeddicord on 2008-12-16
> **Nxion said:**
> Touch is the easiest way to do it.

+1 for just creating blank files. For filling them with stuff, redirect the output of another command:

```
echo "hello" > newfile.log
```

---

### Post by donkyhotay on 2008-12-16
If you want a blank file you can use touch.
```
touch ./myfile.txt
```
Now if you want to add information into the text then you would want to use echo
```
echo -e 'this\n is\n my\n file' >> ./test.txt
```
Echo will create the file too if it doesn't already exist.

---

### Post by Dr Small on 2008-12-16
> **linuxguymarshall said:**
> Is touch a universal Linux (UNIX) command. I want this script to work on ALL Linux systems.
touch should work, as it has been on every distribution I have ever tried.

---

### Post by linuxguymarshall on 2008-12-16
> **donkyhotay said:**
> If you want a blank file you can use touch.
```
touch ./myfile.txt
```Now if you want to add information into the text then you would want to use echo
```
echo -e 'this\n is\n my\n file' >> ./test.txt
```Echo will create the file too if it doesn't already exist.


Thanks. that says it all

---

### Post by donkyhotay on 2008-12-16
touch and echo will work on every system with bash installed which has every version of *nix I've ever used.

---

### Post by linuxguymarshall on 2008-12-16
One more thing. Can I use touch to read a file. For example, I make file x with the line ```
bob=TRUE
``` on line 5

then can I make it read line 5 and 'IF Line 5 = 'TRUE' THEN ; echo "CHEESEPUFFS!" ; ELSE echo "CRAP!"


anyone understand?

---

### Post by donkyhotay on 2008-12-16
Touch doesn't read, it only 'touches' the file which updates the last time the file was accessed but doesn't actually access it. For reading you would need echo again (reversing the arrows will display information to screen) but I don't know how to apply this into a bash 'if' statement.

---

### Post by linuxguymarshall on 2008-12-16
Thanks. I will try and figure it out.

---

### Post by donkyhotay on 2008-12-16
You might try looking at this guide for more detailed information on bash scripting:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by snova on 2008-12-16
'touch' is used to change the timestamps of files, but if the file doesn't exist, it'll create it. This makes it useful for creating empty files.

Alternatively, as suggested, use redirection. There is a Bash builtin, ':', which produces no output and performs no action, that would be suitable:

```
: >newfile
```

echo would do the same thing, but with the possibly incorrect side effect of also writing a blank line. Add the '-n' option to get around that if it matters.

---

### Post by gw7714 on 2009-02-20
I am not a linux pro, but, the command: echo -e 'this\n is\n my\n file' >> ./test.txt 

seems a little complicated.

I need to creat a file in /bin named arch with the contents: uname -m

would typing: sudo echo "uname -m" >arch.txt 

work?

---

### Post by stchman on 2009-02-20
I use the redirect command when inserting text.

The '>' will create a new file called newfile.txt in the users home folder and put the text Hello There in it.
```
echo "Hello There" > ~/newfile.txt
```

The '>>' will append My name is Joe to the newfile.txt in the users home folder
```
echo "My name is Joe" >> ~/newfile.txt
```

Be careful when using the redirect '>' as it will erase the contents of the file.

The touch command can create empty files.

Create a file called newfile.txt in the users home folder.
```
touch ~/newfile.txt
```

Hope this helps.

---

### Post by stchman on 2009-02-20
> **gw7714 said:**
> I am not a linux pro, but, the command: echo -e 'this\n is\n my\n file' >> ./test.txt 

seems a little complicated.

I need to creat a file in /bin named arch with the contents: uname -m

would typing: sudo echo "uname -m" >arch.txt 

work?

Yes the redirect will CREATE a file named arch.txt NOT arch.  In that text file will be the text uname -a.  The \n is a carriage return so the file would look like this:

this
is
my
file

---

### Post by run1206 on 2009-02-20
^^beat me to it lol.  '\n' is a newline char, like "endl" is in c++.

you could make the file in your home folder and copy it over to /bin...
(for example)
```
echo -e 'uname -m' >> ./arch.txt
```
then...
```
sudo cp arch.txt /bin
```

---

### Post by snova on 2009-02-20
```
sudo echo 'uname -m' > /bin/arch
```

Won't work, because the (unprivileged) shell performs redirection. So you could create a temporary file:

```
echo 'uname -m' > arch
sudo mv arch /bin
```

The only thing left to cover is to make sure it's executable, else you can't run it.

```
sudo chmod +x /bin/arch
```

---

### Post by run1206 on 2009-02-20
> **snova said:**
> The only thing left to cover is to make sure it's executable, else you can't run it.

```
sudo chmod +x /bin/arch
```

almost forgot about that, good catch :D

---

### Post by gw7714 on 2009-02-20
Yes! thanks so much! That did it!

---

### Post by gw7714 on 2009-02-20
Darn... I've tried every way it seems.  I know this is'nt the right thread, but has anybody gotten Sun Looking Glass to work with Interpid?

This was my latest method (I found it on a website):

1 create: /bin/arch with content: "uname -m"

2 run: sudo chmod 755 /bin/arch

3 run: sudo apt-get install lg3d-core

Can someone direct me to an apropriate thread?  I've already tried this one:

[http://ubuntuforums.org/showthread.php?t=889756&highlight=Sun](http://ubuntuforums.org/showthread.php?t=889756&highlight=Sun)

---

### Post by gw7714 on 2009-02-20
> **gw7714 said:**
> Yes! thanks so much! That did it!

I should have hit the refresh button on my browser before postin this!

I'll try it.

---

### Post by gw7714 on 2009-02-20
Still get error 1 on Looking glass install...

---

