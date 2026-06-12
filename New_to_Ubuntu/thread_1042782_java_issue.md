---
title: "java issue"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by recycledhippy on 2009-01-17
I am having trouble trying to install java. I keep getting this 

This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

can anyone help me through this I reall not sure what to do. Thanks!!

---

### Post by taurus on 2009-01-17
Click this link, [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u10-docs-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u10-docs-oth-JPR@CDS-CDS_Developer), and check the agreement.  Then, download the **jdk-6u10-docs.zip**.  Once it's done, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
sudo chown root:root jdk-6u10-docs.zip
sudo mv jdk-6u10-docs.zip /tmp
```

---

### Post by recycledhippy on 2009-01-18
then what? It didnt do anything that I can tell

---

### Post by taurus on 2009-01-18
Then maybe try to update your system again.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by recycledhippy on 2009-01-18
Setting up sun-java6-doc (6-07-3ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


I still get this after running updates
:(

---

### Post by recycledhippy on 2009-01-18
when I type this
sudo chown root:root jdk-6u10-docs.zip
nothing happens it just goes to
jason@jason-desktop:~/Desktop$ 
and when I type this
sudo mv jdk-6u10-docs.zip /tmp
the same thing happens

---

### Post by binbash on 2009-01-18
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by recycledhippy on 2009-01-18
this is what I get after doinf what binbash said

Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Norm24 on 2009-01-18
System>Administration>Synaptic Package Manager.

Search for Sun-java6-jre.Mark for installation and then install.Or what binbash said.

---

### Post by recycledhippy on 2009-01-18
did what norm24 said did same thing

---

### Post by Immolatus on 2009-01-18
I think it's easier to just use the openJDK in the repos. There are a lot of docs there as well. I don't know if they are what you are looking for though.

---

### Post by Immolatus on 2009-01-18
Just found something interesting. If you download the doc file from the sun site and just extract it into a folder in your home folder, you can browse it using Firefox by doing /home/whatever and then just naving to it.From there you can view it indexed as opposed to just a big pile of folders. I know this is a bit clumsy but it would work for me.

---

### Post by recycledhippy on 2009-01-19
it seems like nothing I do works I keep getting the same error. Is there a way to remove all java stuff and start over?

---

### Post by stumbleUpon on 2009-01-19
Like taurus said, you have to download the zip file containing the documentation from 

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u10-docs-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u10-docs-oth-JPR@CDS-CDS_Developer)

after agreeing to the license agreement. The file is

```
jdk-6u10-docs.zip
```

In a terminal go to the folder where you have downloaded the file. Change the ownership of the file as mentioned by taurus

```
sudo chown root:root jdk-6u10-docs.zip
```

Copy (or move) the file to /tmp

```
sudo cp jdk-6u10-docs.zip /tmp
```

Of course nothing will be visible on the screeen during these steps.
Once this is done, run
```
sudo aptitude update
```

As you mention, you will get to the point where it says

> Setting up sun-java6-doc (6-07-3ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

Since you already have the file in /tmp press RETURN. Then aptitude finally informs you that the documentation has been installed and you may delete the file in /tmp directory if you wish. 


In case this does not work, try to rename the file in /tmp

```
sudo mv /tmp/jdk-6u10-docs.zip /tmp/jdk-6-doc.zip
```

The sun java docs file was earlier called jdk-6-doc.zip. They seem to have changed the filename. 

In case the renaming does not work, look for the file 'jdk-6-doc.zip' in google. 

Download it and then repeat the steps above.

---

### Post by recycledhippy on 2009-01-19
Once again this did not work. And when I tried to rename it it said I couldn't. Im following these steps exactly as writtin so I know it's not a typping error. please any other ideas?!?! oh yeah, after I try doing this I cant try it a second time without downloading it again. Is this right?

---

### Post by recycledhippy on 2009-01-19
hate to do this but......bump

---

### Post by Terl on 2009-01-19
What is the matter with the versions in Synaptic?  I got java6 doc and sun java 6 sdk right through there.  Just search on jdk and you can find what you need there.

---

### Post by stumbleUpon on 2009-01-20
> **recycledhippy said:**
> Once again this did not work. And when I tried to rename it it said I couldn't. Im following these steps exactly as writtin so I know it's not a typping error. please any other ideas?!?! oh yeah, after I try doing this I cant try it a second time without downloading it again. Is this right?

I really dont understand this. Why cant you rename the file? Can  you please post what it says about not being able to rename the file?

I have done this installation many times and have never had this problem. 

Now I actually uninstalled the sun-java6-doc package, downloaded the same file that was mentioned in the earlier links (jdk-6u10-docs.zip), changed the ownership to root and moved it to /tmp directory. I then tried to install the package (sudo aptitude install sun-java6-doc). It came to the point where aptitude asked for the downloaded documentation file. I pressed RETURN but it complained that it could not find the file. So i renamed the file (sudo mv /tmp/jdk-6u10-docs.zip /tmp/jdk-6-doc.zip) and then pressed RETURN. It worked. No problem.


I think that you are doing some mistake in the steps. If not, i dont know the solution. Sorry.

---

### Post by akhayat on 2009-01-22
This worked for me...thanks! :)

---

