---
title: "installing a program?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by MatthewVC on 2010-06-17
I'm using linux to run several bioinformatics programs.  I'm trying to install one, but I'm completely lost when trying to do it. 

The program is called Cufflinks. From the program's website ([http://cufflinks.cbcb.umd.edu/tutorial.html](http://cufflinks.cbcb.umd.edu/tutorial.html)) 
> In order to make it easy to install Cufflinks, we provide a few binary packages to save users from occasionally frustrating process of  building Cufflinks, which requires that you install the Boost libraries.  To  use the binary packages, simply download the appropriate one for your  machine, untar it, and place the cufflinks and cuffcompare  binaries in your PATH environment variable.the files in the tar have no file extension....  should I change that?  Also, what is a "PATH environment variable"? and how do I move things there?????

Thanks for any insight you can give

Matt

---

### Post by Saint_ on 2010-06-17
Hm I got it to run just through the terminal, (not sure if thats what you want) so what you'd do is download the Linux x86_64 binary and then extract what's inside there to like your desktop or home directory. Then in the terminal type (In this example the folder is in my home directory: ```
cd cufflinks-0.8.2.Linux_x86_64/
``` and then type ```
./cufflinks <arguments here>
``` Hope this helps a bit

---

### Post by flowheat on 2010-06-17
Try to navigate to the binary files in a terminal window and type:

```
./ <name of binary file>
```

./ is basically the run command in Unix.

If that works then you can look into making a shortcut to run that command more easily.

Don't be concerned that there's no file extensions either.  That's normal in a Unix world.

You can look here for a further explanation:

[http://en.wikipedia.org/wiki/Filename_extension]("http://en.wikipedia.org/wiki/Filename_extension")

---

### Post by elysianfields44 on 2010-06-17
> **MatthewVC said:**
> the files in the tar have no file extension....  should I change that?

Nope, the files have no extensions because they are scripts.

> Also, what is a "PATH environment variable"? and how do I move things there?????


Here's an introduction to environment variables: [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

PATH is an environment variable. The reason they are asking you to add cufflinks to the PATH is so that you can run the cuffcompare, cuffdiff and cufflinks scripts from anywhere (from any folder). 

Here's what I mean: if you don't add anything to PATH, you will be able to do the following (for example if you want to run cuffcompare), as the above posters suggested:

```

cd /path/to/cufflinks/folder
./cuffcompare somefile.sam

```

However, if you add the /path/to/cufflinks/folder to your PATH variable, bash will know to look for scripts in that particular path without explicitly navigating to it. i.e. you would be able to use the scripts from ANY directory, simply like this:

```

cuffcompare somefile.sam

```

And here's how to add a path to the PATH variable:

```

sudo gedit ~/.bashrc

```

At the end of the file, add the following lines:

```

PATH=$PATH:/path/to/cufflinks/folder
export PATH

```

where you replace /path/to/cufflinks/folder with the appropriate absolute path. Then save and close the file, and run the following:

```

source ~/.bashrc
echo $PATH

```

The output of the last command should include the path to cufflinks that you just added.

Hope that helps.

---

### Post by nothingspecial on 2010-06-17
> **elysianfields44 said:**
> 

```

cuffcompare somefile.sam

```

And here's how to add a path to the PATH variable:

```

sudo gedit ~/.bashrc

```

At the end of the file, add the following lines:

```

PATH=$PATH:/path/to/cufflinks/folder
export PATH

```

where you replace /path/to/cufflinks/folder with the appropriate absolute path. Then save and close the file, and run the following:

```

source ~/.bashrc
echo $PATH

```

The output of the last command should include the path to cufflinks that you just added.

Hope that helps.

Or you could just move cufflinks into /bin or /usr/bin which may seem a little less daunting to a beginner. (They are already in your path).

---

### Post by MatthewVC on 2010-06-17
I did as Nothing outlined, but the command still doesn't work.  

I also tried just moving the files into the bin folder, and I got a permission denied message, I'm guessing I have to set admin permission somewhere?  

Thanks,
Matt

---

### Post by quinnten83 on 2010-06-17
to move them, open a terminal and type gksudo nautilus
type your password and copy paste in the new nautilus window.

---

### Post by nothingspecial on 2010-06-17
> **MatthewVC said:**
> I did as Nothing outlined, but the command still doesn't work.  

I also tried just moving the files into the bin folder, and I got a permission denied message, I'm guessing I have to set admin permission somewhere?  

Thanks,
Matt

You have to make to file have permission to run.

I`m sorry, I should have included this in my first post.

The command is sudo chmod +x *file*

I don`t know now where your file is.

If it is in /bin

 then ```
sudo chmod +x /bin/cufflinks
```

or if you have put in /usr/bin/ then

```
sudo chmod +x /usr/bin/cufflinks
```

I`m sorry if I have confused rather than helped.

---

### Post by MatthewVC on 2010-06-17
Perfect! got it!  

thanks for all your help.  Now I just have to figure out how to use the program.....  ;-)

---

