---
title: "How do I install a Java bin file?"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by ArnoldGove on 2009-06-10
How do I install this file?

jre-6u3-linux-i586.bin

It installs Java, required for a game.

---

### Post by kwacka on 2009-06-10
Take a look at 'the perfect desktop' at howto forge [URL="http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04"]link here.
[/URL]

Explains java and several other useful applications.

---

### Post by ArnoldGove on 2009-06-10
I'm not online with Ubuntu, so I downloaded the required bin file 'manually' (on another system). How do I install it in Ubuntu?

---

### Post by shifty_powers on 2009-06-10
is that specific version required?

otherwise then ubuntu-restricted-extras will install java and lots of other useful stuff...

---

### Post by ArnoldGove on 2009-06-10
> **shifty_powers said:**
> is that specific version required?

otherwise then ubuntu-restricted-extras will install java and lots of other useful stuff...

The specific file was referenced by the game, and a script (?) linked to it. So I downloaded it on another system, and transferred it.

I don't know what 'ubuntu-restricted extras' are.

Recall that I'm not online with Ubuntu.

---

### Post by ibutho on 2009-06-10
Change into the directory where you saved the java runtime environment and enter
```
chmod +x jre-{VERSION}.bin
./jre-{VERSION}.bin
sudo mv jre{VERSION} /opt/.
sudo update-alternatives --install /usr/bin/java java /opt/jre{VERSION}/bin/java 2
sudo update-alternatives --config java

```
Replace {VERSION} with the actual version of the jre e.g. mine is 1.6.0_14. When you run the last command, you should see something like
```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-sun/jre/bin/java
*         2    /opt/jre1.6.0_14/bin/java

Press enter to keep the default[*], or type selection number: 

```
Choose the version to make default.

---

### Post by colorpurple21859 on 2009-06-10
do the following commands;
sudo cp -a <location of bin file> /usr/jre-6u13-linux-i586.bin
cd /usr
sudo chmod a+x  jre-6u13-linux-i586.bin
sudo ./ jre-6u13-linux-i586.bin
sudo ln -s /usr/jre1.6.0_13/bin/java /java/bin

the first commands copies the file to /usr
third command makes sure it is executable
have to agree to terms of sun-java after issue of fourth command
last command makes a link to the java command in your path directory /usr/bin

---

### Post by colorpurple21859 on 2009-06-10
on my last reply edit the last command to be
sudo ln -s /usr/jre1.6.0_13/bin/java /usr/bin/java

---

### Post by TrakerJon on 2009-06-10
Start by going to System > select Administration > select Software Sources > Check the first four boxes under the Ubuntu Software and Updates tabs then Close and Reload

Then from a terminal window install the latest Sun Java JRE by typing...

**sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts**

---

### Post by t0p on 2009-06-10
My advice is to forget that java binary you downloaded, and instead install the latest Sun JRE from the repositories.

Do this by opening the terminal and type in:

```
sudo apt-get install sun-java6-bin
```

When you install software from random sites, you run the risk of making your system unstable.  Getting software from the repos (either through apt-get or System > Administration > Synaptic) removes this danger.  Also, you're unlikely to unwittingly install malware if you get your stuff from trusted sources like the official repos.

---

### Post by ibutho on 2009-06-13
> **t0p said:**
> My advice is to forget that java binary you downloaded, and instead install the latest Sun JRE from the repositories.

Do this by opening the terminal and type in:

```
sudo apt-get install sun-java6-bin
```

When you install software from random sites, you run the risk of making your system unstable.  Getting software from the repos (either through apt-get or System > Administration > Synaptic) removes this danger.  Also, you're unlikely to unwittingly install malware if you get your stuff from trusted sources like the official repos.

In one of his posts above, the guy said that his Ubuntu machine does not have internet access, which means that he cannot access the online repos. The java binary does not interfere with any other software and is not from a random site (its an official package from java.sun.com which can be installed on any Linux distro).

---

