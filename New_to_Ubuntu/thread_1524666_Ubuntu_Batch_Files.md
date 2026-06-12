---
title: "Ubuntu Batch Files"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by borth92 on 2010-07-05
I am not a noob to ubuntu, but theres one thing I have never known how to do. I need to make a file that runs multiple commands in the terminal. That way I can limit my typing and just click one file to run all the commands I need. In Windows there is just the .bat extension but I do not know how to accomplish this in Ubuntu.

These are the commands I want the program to do:

deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main
sudo apt-get update
sudo apt-get install burg
gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -
sudo burg-install /dev/sda
sudo update-burg

---

### Post by s.fox on 2010-07-05
Hello,

I would create a shell script.  [This]("http://ubuntuforums.org/showthread.php?t=217328") should give you some ideas. :)

If you have any troubles please post back.

-Silver Fox

---

### Post by Hanzerik on 2010-07-05
In linux .bat .cmd are called scripts. They can be named anything, but for simplicity and accountability, they usually end with a .sh, but can have any type of extension or non at all. The only requirement is that they be readable by the shell. Which usually means they are plain old text files filled with one or more commands. They also need to have execute permissions assigned: 0755 is the most common permissions assigned (Owner has Read/Write/Exec, Group and Others have Read/Exec). You can change permissions via the cli with chmod, or can use file managers like Nautilus to change permissions.

Very simple example of creating a script:
```

echo "Hello Ubuntu" > TestScript.sh
chmod 755 TestScript.sh
./TestScript.sh
Hello Ubuntu

```

Script #1 AddSource.sh (**You just need to do this one once**)
```

#!/bin/bash
sudo echo "deb http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main" >> /etc/apt/sources.list
sudo echo "deb-src http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main" >> /etc/apt/sources.list

```

Or....you could just open up /etc/apt/sources.list in your favorate text editor and add the two lines to the bottom manually. Save the file, then run the second script.
```

gksudo gedit /etc/apt/sources.list

```

Script #2 InstallBurg.sh
```

#!/bin/bash
sudo apt-get update
sudo apt-get install burg
gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -
sudo burg-install /dev/sda
sudo update-burg

```

Change permissions of AddSources.sh and InstallBurg.sh to be executable
chmod 755 AddSources.sh
chmod 755 InstallBurg.sh

Run the scripts
./AddSources.sh
./InstallBurg.sh

Not sure what Burg is, but if you already have the commands typed out like you do, then you can cut and paste into a terminal...

---

### Post by Elfy on 2010-07-05
Can I just add that there's an easy way to add the repo and get the key

```
sudo add-apt-repository ppa:bean123ch/burg
```

Personally I'd not see the point in setting up a script to do a single task.

If you found that you needed to install and update burg once it was installed an alias would be sufficient I think.

---

### Post by Paqman on 2010-07-05
It might be worth explaining what these lines actually do:

> **borth92 said:**
> 
deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main


These are the locations of the PPA containing the packages. Needs to be added to sources.list and then:

> sudo apt-get update

Prompts the package manager to rescan all the available sources, including the new PPA.

> sudo apt-get install burg

Installs the package burg

> gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -

Obtains the authentication key for the PPA, so that the package manager knows it is connecting to a valid source. This should be done before the apt-get update and the install, or APT will complain.

> 
sudo burg-install /dev/sda
sudo update-burg

Specific commands for the burg package.

You can see from the above that all except the last command are one-off events. The only thing you'd need to do more than once is "sudo update-burg". There's no reason you couldn't make a shell script containing just that one line.

---

### Post by borth92 on 2010-07-05
The idea was I wanted to be able to made a script to switch between burg and grub. Any time my grub updates it makes itself the standard boot loader and I need to reinstall burg to make it the standard one again. That would be very easy with just one script.

---

### Post by sisco311 on 2010-07-05
> **borth92 said:**
> The idea was I wanted to be able to made a script to switch between burg and grub. Any time my grub updates it makes itself the standard boot loader and I need to reinstall burg to make it the standard one again. That would be very easy with just one script.

For that you don't have to re-add the repository, just run:
```
sudo dpkg-reconfigure -u burg-pc
```

But if burg works for you why don't you remove grub2?

---

### Post by lkjoel on 2010-07-05
> **borth92 said:**
> I am not a noob to ubuntu, but theres one thing I have never known how to do. I need to make a file that runs multiple commands in the terminal. That way I can limit my typing and just click one file to run all the commands I need. In Windows there is just the .bat extension but I do not know how to accomplish this in Ubuntu.

These are the commands I want the program to do:

deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main
sudo apt-get update
sudo apt-get install burg
gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -
sudo burg-install /dev/sda
sudo update-burg
```
#!/bin/bash
echo "deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main" >> /etc/apt/sources.list
echo "deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) lucid main" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install burg
gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -
sudo burg-install /dev/sda
sudo update-burg
```
Save that into a file named yourfile.sh
Go into a Terminal (Applications->Accessories->Terminal) window:
```
chmod +x yourfile.sh
./yourfile.sh
```
If you have installed Terminal Enhancements 0.1.1b from my sig, type:
```
chmod +x yourfile.sh
yourfile.sh
```

---

### Post by borth92 on 2010-07-05
> **sisco311 said:**
> For that you don't have to re-add the repository, just run:
```
sudo dpkg-reconfigure -u burg-pc
```But if burg works for you why don't you remove grub2?

Because I removed the recovery option in burg so if i want to use it i need to go back to grub

---

### Post by sisco311 on 2010-07-05
> **borth92 said:**
> Because I removed the recovery option in burg so if i want to use it i need to go back to grub

To boot into Recovery Mode, at the burg menu highlight the normal Ubuntu entry, press e for edit, replace the **quiet splash** boot options with **single**, press Ctrl+x to exit then Enter to boot.

---

### Post by borth92 on 2010-07-06
> **sisco311 said:**
> To boot into Recovery Mode, at the burg menu highlight the normal Ubuntu entry, press e for edit, replace the **quiet splash** boot options with **single**, press Ctrl+x to exit then Enter to boot.

I have another question thats more specific to burg, are you familiar with burg?

---

### Post by sisco311 on 2010-07-06
> **borth92 said:**
> I have another question thats more specific to burg, are you familiar with burg?

Perhaps start a new thread with an appropriate title for your question and you will get more responses. Post a link to the thread here, I will try to help.

---

