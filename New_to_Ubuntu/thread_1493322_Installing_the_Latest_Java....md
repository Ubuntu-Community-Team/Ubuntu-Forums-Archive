---
title: "Installing the Latest Java..."
date: 2010-05-25
forum: New to Ubuntu
---

### Post by chome4 on 2010-05-25
Is there an easier way of installing the latest version of Java than this:


[LIST=1]
[*]**Change the permission of the file you downloaded to be executable.** Type:
  chmod a+x jre-6u<version>-linux-i586.bin
[*]Verify that you have permission to execute the file. Type:
ls -l
[/LIST]
 			 	         		 		 	     	     	 	     	     	         		 		 			 [CENTER][IMG]http://www.java.com/en/img/download/linux_image2.gif[/IMG][/CENTER]
 		 	     	     	 	     	     	        	 			

[LIST=1]
[*]**Change to the directory in which you want to install.** Type:
    cd <directory path name>
    For example, to install the software in the /usr/java/ directory, Type:
    cd /usr/java/

    ***Note about root access:** To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions.*
[/LIST]
 			 	         		 		 	     	     	 	     	     	        	 			
[LIST=1]
[*]**Run the self-extracting binary** Type:
  ./jre-6u<version>-linux-i586.bin

  The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter **yes** to proceed with the installation.
[*]Java is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_<version> directory. When the installation has completed, you will see the word **Done**.
[/LIST]
=====================================================

Is there a location I can download and run the deb version?

---

### Post by cavh on 2010-05-25
Applications => Ubuntu Software Centre => Get Free Software => Other => Ubuntu restricted extras.

See screenshot attached.

HTH,

Clive

---

### Post by chome4 on 2010-05-25
Under 'Applications' I don't have 'Ubuntu Software Centre'

---

### Post by clhsharky on 2010-05-25
chome4


[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Sharky

---

### Post by chome4 on 2010-05-25
Thank you.

---

