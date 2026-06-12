---
title: "help comparing files"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by neurostu on 2010-03-08
I recently moved a large number of files (over 1tb of data) from one computer to another.

On the old computer I ran the command:
```


 find data/  -ls  > /tmp/data.dir

```

and then I ran the same command on my new computer. The order in which the files are listed isn't the same and the ownership is different so I can't diff the two /tmp/data.dir files.

All I want to do is compare all the files listed in the .dir files and compare their sizes. What is the easiest way of doing this?

I can't run a new command on the old computer. All I have to work with is the old contents of /tmp/data.dir


thanks

---

### Post by 2hot6ft2 on 2010-03-08
Assuming you can access both folders on 1 pc or by connecting by ssh or something
```
sudo apt-get install krusader
```
krusader is a twin panel file manager so you can view the contents of 2 folders at the same time and even synchronize them using Tools > Synchronize Directories.
Once you start synchronize you can scroll down the list and see any that are different before actually synchronizing them.

After installing it will be in
Applications > Accessories > Krusader

Using krusader with ssh
krusader (Kubuntu)
Tools > New Net Connection
Protocol: fish://
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Click on Connect

---

### Post by r-senior on 2010-03-08
You can use awk to pick out columns from the listing:

$ find . -ls | awk '{print $7" "$11}'

or 

$ cat /tmp/data.dir | awk '{print $7" "$11}' > /tmp/data_name_and_size.dir

And you can pipe through sort to correct the sort order:

$ cat /tmp/data.dir | awk '{print $11" "$7}' | sort > /tmp/data_name_and_size_sorted.dir

---

### Post by doas777 on 2010-03-08
just for finding duplicates, I've been using fslint.

---

### Post by neurostu on 2010-03-09
> **r-senior said:**
> You can use awk to pick out columns from the listing:

$ find . -ls | awk '{print $7" "$11}'

or 

$ cat /tmp/data.dir | awk '{print $7" "$11}' > /tmp/data_name_and_size.dir

And you can pipe through sort to correct the sort order:

$ cat /tmp/data.dir | awk '{print $11" "$7}' | sort > /tmp/data_name_and_size_sorted.dir
I used this and then meld to do compare the differences, this worked perfectly. Thanks!

---

