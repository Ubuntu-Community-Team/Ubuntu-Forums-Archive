---
title: "Javascript help"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by wyrfxrssn on 2008-12-11
I'm trying to install Javascript on my computer, but I can't figure out how. I got it from here [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp), I downloaded the first one in the Linux category. I looked at the installation instruction link on the right, but I can't figure it out. It says:

 To install the Linux RPM (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java

      Note about root access: To install the JRE in a system-wide location such as/usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586-rpm.bin
   5. Start the installation process. Type:
      ./jre-6u<version>-linux-i586-rpm.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   6. The installation file creates jre-6u<version>-linux-i586.rpm file in the current directory.



RPM unpacking completes

   7. Run the RPM command at the terminal to install the packages. Type:
      rpm -iv jre-6u<version>-linux-i586.rpm
   8. The JRE is installed in jre1.6.0_<version> sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.6.0_<version> directory. Verify that the jre1.6.0_<version> sub-directory is listed under the current directory. Type:
      ls



Verify the installation filename

The installation is now complete. Go to the Enable and Configure section.

I don't know a thing about directories and whatnot, can someone help explain this?

---

### Post by cardinals_fan on 2008-12-11
First, you're trying to install Java, which is very different from javascript.

Follow these instructions: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by wyrfxrssn on 2008-12-11
Yeah, your right. I got it installed the way it told me to, but NOW I can't figure out how to activate it. The instructions it gives me are here: [http://java.com/en/download/help/5000010500.xml#14](http://java.com/en/download/help/5000010500.xml#14)
I can't find the mozilla directory, it's not in lib.

---

### Post by cardinals_fan on 2008-12-11
> **wyrfxrssn said:**
> Yeah, your right. I got it installed the way it told me to, but NOW I can't figure out how to activate it. The instructions it gives me are here: [http://java.com/en/download/help/5000010500.xml#14](http://java.com/en/download/help/5000010500.xml#14)
I can't find the mozilla directory, it's not in lib.
Try /usr/lib/firefox-3.0.3  [http://packages.ubuntu.com/intrepid/i386/firefox-3.0/filelist](http://packages.ubuntu.com/intrepid/i386/firefox-3.0/filelist)

---

### Post by Separ on 2008-12-11
Easy way to install java:
```
sudo apt-get install sun-java6-jre sun-java6-bin
```
To find where programs are, use the command 'whereis' from the terminal.
eg:```
whereis firefox
```

Protip: .rpm files are associated with red-hat based systems, not debian which is what ubuntu is based on. You want .deb files to install things. There is however a program available in the repos that can convert a .rpm into a .deb but it can be flakey. It is called alien.

---

### Post by weweboom on 2008-12-22
Hi zack!

---

