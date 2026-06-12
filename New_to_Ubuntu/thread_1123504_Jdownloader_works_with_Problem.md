---
title: "Jdownloader works with Problem"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by kemo0o on 2009-04-12
i installed Jdownloader soon it works perfectly from the terminal as i type 
> sudo ./jd.shbut while i am making Launcher for it , it asks me where i want to save files (default save location)

then it gives me message  as shown in pic. 

[IMG]http://i39.tinypic.com/211uypu.jpg[/IMG]

Why and how can i solve this ???

---

### Post by kemo0o on 2009-04-12
Also How could i save Files out of root (To External drive or /media) or other Partitions??

---

### Post by aktiwers on 2009-04-12
Its a bad idea to run it as root. Don't run apps as root if it's not needed.

Install it as user (in your home folder) and run it from there as user. Thats what I do :)

---

### Post by kemo0o on 2009-04-12
whould you be so kind ad clearify more (instructions)... am still newbie

---

### Post by mikewhatever on 2009-04-12
You should be able o run the program without sudo, that is jd.sh only. As for the launcher problem, there seems to be some confusion. Creating a launcher doesn't require saving files. Can you describe the steps in more details to give us an idea of what's going on.

---

### Post by kemo0o on 2009-04-12
i installed the JDownloader as explained in this link :
[http://blackonsole.blogspot.com/2009/03/install-jdownloader-on-linux-ubuntu-810.html](http://blackonsole.blogspot.com/2009/03/install-jdownloader-on-linux-ubuntu-810.html)
OK. 
The last step to make launcher , i made it but when i try to run it , then choose Default save location the message above in the picture appear

---

### Post by RuleMaker on 2009-04-12
If you have to run it as root (I dont suggest that) you must be the owner of the directory where you will save the files or at least you must have the write permissions.
So, what you need to do is:
```
sudo chown -R <save_directory_name>
```
or:
```
sudo chmod +w <save_directory_name>
```
or (would be the best):
install the JDownloader again as user and run it as user. (I'm doing it that way).

---

### Post by kemo0o on 2009-04-12
> install the jdownloader again as user and run it as user. (i'm doing it that way).
how ????

---

### Post by mikewhatever on 2009-04-12
> **kemo0o said:**
> 
The last step to make launcher , i made it but when i try to run it , then choose Default save location the message above in the picture appear

Why not follow the instructions you posted a link to? Creating a launcher is straight forward and doesn't include running the program. I don't think you need to reinstall jdownloader, just run it as a normal user, without sudo.

---

### Post by kemo0o on 2009-04-12
> Why not follow the instructions you posted a link to? Creating a launcher is straight forward and doesn't include running the program. I don't think you need to reinstall jdownloader, just run it as a normal user, without sudo.
when i do that the message appear !! i applied the explained but as i said after creating the launcher the message appear but if i use "sudo" it works good

---

### Post by mikewhatever on 2009-04-12
The message about permissions seems to be related to the default saving location and is completely unrelated to the launcher creation. It looks like the launcher works fine, the program runs and asks you where you'd like to save files. I think everything will work if you create a 'Downloads' folder in your home directory and point jdownloader there.

---

### Post by aktiwers on 2009-04-12
I don't even use an sh file actually?

1) Just download the zip file:
[http://bluehost.to/file/WLIJkgT7l/JDownloader_0.4.936.zip](http://bluehost.to/file/WLIJkgT7l/JDownloader_0.4.936.zip)

2) Drag it to your homefolder and right-click and extract it.

3) Delete the Zip file

4) Go to the new Jdownloader folder and right-click the JDownloader.jar file.
Pick "open with" and then "Sun Java runtime 6"

Done!

---

### Post by RuleMaker on 2009-04-13
> **kemo0o said:**
> how ????

I don't see the reason why people are looking all over the net to find something that is so simple and published on official sites.

First of all we are going to remove your old install.

```
sudo rm -rf /opt/jdownloader
```

next...

Download this script [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh) (this is from official website).

and put it on your desktop

now do this:
```

sudo apt-get install wget
cd $HOME/Desktop
sudo chmod +x jd.sh
bash jd.sh
```

Now you should see the installer apperaring, downloading and installing stuff.
After it completes give us the otput of:
```
ls -a $HOME/.jd
```

Now do this step-by-step and be VERY CAREFUL and don't skip any step.
(commands are executed one line per 1 execute).

---

### Post by scan1 on 2009-06-21
you can create a launcher

command should be:
```

java -jar /home/user/jdownloader/JDownloader.jar
```

---

