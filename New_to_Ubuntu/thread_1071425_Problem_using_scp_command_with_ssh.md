---
title: "Problem using scp command with ssh"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by TAFKARS on 2009-02-16
Hi there

Despite searching through here and google for the answer (which all seem to point to what I am doing), can anyone suggest what I might be doing wrong with the following?

I simply want to copy a file from my office desktop to my home laptop using ssh. I have tried a range of scp commands in line with what I have read online from other sites, but none seem to work and the general response seems to be:

scp -P 23 mydesktop_username@officeIP /some/local/Documents/Test/fileineed.bst: ~/Desktop/


cp: cannot stat `mydesktop_username@officeIP': No such file or directory
cp: cannot stat `/some/local/Documents/Test/fileineed.bst:': No such file or directory

I have tried other alternatives to the :~/Desktop/, just to see if I can get scp to work, including typing the full pathway and home laptop IP as the other examples have indicated, but I still get the 'cannot stat' error.

I am using port 23 deliberately.

Can anyone suggest the definitive way of doing this and the typical circumstances under which this works?

Many thanks in advance!

---

### Post by spiderbatdad on 2009-02-16
I like to use sftp over ssh session for this. Connect to your server with
```
sftp user@ipaddress
```gives you an sftp> prompt. You can use regular terminal commands to navigate the file system and so forth, and put and get commands for file transfers.```
put /some/file /path/to/put
```You can also just drag and drop files into the terminal window.

You can aslo connect graphically by going to Places>>Connect To Server. Select ssh from the drop down window. Input user name and ip address. This should mount the file system on your desktop. You can bookmark it in nautilus. Unmount the volume properly with right click "unmount volume."

---

### Post by mister_pink on 2009-02-16
Firstly, can you ssh?

Next, that command seems to have spaces in odd places. It should be, if you're at home copying from work:
```

scp -P 23 youruser@yourofficeip:~/fileonyourofficepc ~/placeonhomepc

```
or something similar. Note only spaces between the two places, like a normal copy command. You'll also have issues if there's any spaces in filenames.

---

### Post by TAFKARS on 2009-02-16
> **spiderbatdad said:**
> I like to use sftp over ssh session for this. Connect to your server with
```
sftp user@ipaddress
```gives you an sftp> prompt. You can use regular terminal commands to navigate the file system and so forth, and put and get commands for file transfers.```
put /some/file /path/to/put
```You can also just drag and drop files into the terminal window.

You can aslo connect graphically by going to Places>>Connect To Server. Select ssh from the drop down window. Input user name and ip address. This should mount the file system on your desktop. You can bookmark it in nautilus. Unmount the volume properly with right click "unmount volume."

Many thanks for this, I'll try it shortly and post how I get on... :)

---

### Post by TAFKARS on 2009-02-16
> **mister_pink said:**
> Firstly, can you ssh?

Next, that command seems to have spaces in odd places. It should be, if you're at home copying from work:
```

scp -P 23 youruser@yourofficeip:~/fileonyourofficepc ~/placeonhomepc

```
or something similar. Note only spaces between the two places, like a normal copy command. You'll also have issues if there's any spaces in filenames.

Thanks for the tip,yes ssh connection is made without a problem. It probably is an incorrect space somewhere (though my test file has no spaces in it). As with the previous helper, I'll give it a try and post how I get on. Cheers!

---

### Post by prshah on 2009-02-16
> **TAFKARS said:**
> ```

scp -P 23 [color=red]mydesktop_username@officeIP /some/local/Documents/Test/fileineed.bst:[/color] ~/Desktop/
                                    [color=blue][SIZE="3"]/\[/SIZE][/color]
```

You have the spacing and the syntax wrong; the correct command will be```


scp -P 23 mydesktop_username@officeIP[color=red]:[/color]/some/local/Documents/Test/fileineed.bst ~/Desktop/
                                     [color=blue][SIZE="3"]/\[/SIZE][/color]
```

Note the ":" between your desktop reference and the filename, and the space between the source filename and the destination.

And also remember that case sensitivity is important for filenames as well as usernames.

---

### Post by anaconda on 2009-02-16
I prefer to use 
sshfs if I want to copy files...

with sshfs you can mount the filesystem over an ssh connection, and then copying works just like the remote computer would be a folder on your machine..

---

### Post by TAFKARS on 2009-02-16
> **prshah said:**
> You have the spacing and the syntax wrong; the correct command will be```


scp -P 23 mydesktop_username@officeIP[color=red]:[/color]/some/local/Documents/Test/fileineed.bst ~/Desktop/
                                     [color=blue][SIZE="3"]/\[/SIZE][/color]
```

Note the ":" between your desktop reference and the filename, and the space between the source filename and the destination.

And also remember that case sensitivity is important for filenames as well as usernames.

Thanks for the reply, though the scp command still does not work despite me typing EXACTLY as you have suggested! Apparently the file I tried to copy does not exist (despite the fact I can see it...)

Time to try the other suggestions :)

---

### Post by TAFKARS on 2009-02-16
> **mister_pink said:**
> Firstly, can you ssh?

Next, that command seems to have spaces in odd places. It should be, if you're at home copying from work:
```

scp -P 23 youruser@yourofficeip:~/fileonyourofficepc ~/placeonhomepc

```
or something similar. Note only spaces between the two places, like a normal copy command. You'll also have issues if there's any spaces in filenames.

Strange one this. The file copied, but placed the copied file on the Desktop of my office machine, rather than the desktop of my home laptop :confused:. Almost as if its not recognising that I am 'sshing'(pardon the phrase)?

The turn of sftp now...

---

### Post by TAFKARS on 2009-02-16
Well, for whatever reason I could not remotely connect through sftp, I tried to connect through port 23 as it had been set up, but it seemed to want to connect through port 22 and clearly was unable.

Are there any further comments regarding the syntax or spacing in light of my attempts to try the previous suggestions?

Cheers for all the replies so far, appreciate the help.

---

### Post by bodhi.zazen on 2009-02-16
first, are you sure you set up ssh on port 23 (the default is 22).

At any rate, the error messages in your first post indicate the problem is that you have not typed the path to the files you wish to transfer.

The syntax is 

scp source destination

or to be more specific

scp local_file user@server:/server/location

For example, to copy a file "foo" to your home directory on the server 

scp -P 23 foo user@server:/home/user

where "user" == your user name on th eserver
"server" == your server IP address

If you do not know the path, use tab completion.

---

### Post by TAFKARS on 2009-02-16
> **bodhi.zazen said:**
> first, are you sure you set up ssh on port 23 (the default is 22).

At any rate, the error messages in your first post indicate the problem is that you have not typed the path to the files you wish to transfer.

The syntax is 

scp source destination

or to be more specific

scp local_file user@server:/server/location

For example, to copy a file "foo" to your home directory on the server 

scp -P 23 foo user@server:/home/user

where "user" == your user name on th eserver
"server" == your server IP address

If you do not know the path, use tab completion.

Thanks for the reply, though I am trying to do the opposite (i.e. copy files on server to home laptop). All variations on this seem to have failed via the CLI, but the good news is that I have solved the problem using the Places>Connect to server suggestion made earlier. Not sure why I was unable to connect this way before as per my previous post, but I don't really care as all is working and all is well in sunny Devon.

Massive thanks to all who replied. You are all on my Christmas card list :KS:KS:popcorn:

---

