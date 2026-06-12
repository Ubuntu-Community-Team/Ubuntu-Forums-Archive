---
title: "How to browse folders in CLI??!"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-21
This is a totally ridiculous question, I'm aware of that, but I can't browse folders in my CLI! I know the commands goes "cd /folder", but every time I enter that command, I get the notification that that folder does not exist, I know it exists in that location (im sure), I do "dir" and I get the folders in that folder, but when I do"cd /that folder" it errors me!
WTF, this frustrates me a lot, could somebody tell me something more about browsing folders in CLI? I've browsed and googled, but no useful topic on this issue.

---

### Post by howefield on 2009-01-21
Forgive me if this is too silly, but remember the folders are case sensitive, Desktop is different to desktop, ect, ect.

---

### Post by Dr Small on 2009-01-21
It's done like this:
```
[drsmall@darkghost ~]$ ls
bin  e-Sword  media
[drsmall@darkghost ~]$ cd media/
[drsmall@darkghost media]$ 

```

By running "cd /folder" you are accending to the / (root directory) and then into folder. If it doesn't exist, of course you will be receiving an error. Try removing the slash for directories in the same directory you are located.

---

### Post by Ben Page on 2009-01-21
> **howefield said:**
> Forgive me if this is too silly, but remember the folders are case sensitive, Desktop is different to desktop, ect, ect.

I know, I have tried everything, even all caps (desperate), without "cd", as root, as user...
Note, that this happens to me on every linux I have tried, so I know its me that is doing something wrong. I know my MSDOS, but this I just cant digest right

---

### Post by oldos2er on 2009-01-21
Use the Tab key for file (and folder) name completion.

 If there's a leading "/" in a folder name (e.g. /home), it tells bash to look for the folder from the root directory. / = root.

---

### Post by Ben Page on 2009-01-21
> **Dr Small said:**
> It's done like this:
```
[drsmall@darkghost ~]$ ls
bin  e-Sword  media
[drsmall@darkghost ~]$ cd media/
[drsmall@darkghost media]$ 

```

By running "cd /folder" you are accending to the / (root directory) and then into folder. If it doesn't exist, of course you will be receiving an error. Try removing the slash for directories in the same directory you are located.

Damn it! I knew it was easy, but I have never remembered not to write "/" in front of folder! Stupid! Thnx, this works!

...on every manual it says "cd /folder/"...

---

### Post by Ben Page on 2009-01-21
> **oldos2er said:**
> Use the Tab key for file (and folder) name completion.

 If there's a leading "/" in a folder name (e.g. /home), it tells bash to look for the folder from the root directory. / = root.

There should be a short introduction to all this little, but wery useful stuff, there is only "more advanced" manuals, but everybody assumes that one should know his basic CLI, it is basic, but you don't born with it. :)

---

### Post by s|fr on 2009-01-21
Hi Ben,

in *nix "/" means root path (i-e the highest level of directory you can ever have). When you type cd /folder, you are actually telling the cli to go into a folder called "folder" on the root path. This is unlikely to work unless the "folder" is something of a standard liek etc or dev or home. The reason I say this is because ubuntu by default restricts manipulation of pretty much most things outside your own directory.

I found this [link]("http://4.bp.blogspot.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600-h/linux_file_structure.jpg"). It is helpful in mapping out how the file structure is in linux.
Also if you are going to play around with folders and files in cli I'll also recommend that you:

```

sudo apt-get install mc

```

This will install midnight commander which is a cli based directory explorer. it will be of helpful while you learn your way around the cli.

Also found this [video tutorial]("http://www.youtube.com/watch?v=sl6EGVTL9IAhttp://") which might be helpful.

and this [tutorial]("http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-cd.html").

Hopefully all these links will give a  good idea of how to switch directories in cli.

Hope that helps.

---

### Post by donkyhotay on 2009-01-21
> **Ben Page said:**
> I know, I have tried everything, even all caps (desperate), without "cd", as root, as user...
Note, that this happens to me on every linux I have tried, so I know its me that is doing something wrong. I know my MSDOS, but this I just cant digest right

Can you post the command you're typing here along with the results of ls? Then we might be able to figure out what you are doing wrong.

//edit: nevermind, looks like this has already been done and issue resolved.

---

