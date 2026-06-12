---
title: "which java to download for Ubuntu - ?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-15
choices are and i quote below

	Linux
			
	Linux RPM (self-extracting file) filesize: 19.39 MB 	Instructions 	
Verify Now
 
After installing Java, restart your browser and verify Java has been installed correctly.
	Linux (self-extracting file) filesize: 19.89 MB 	Instructions
	Linux x64 * filesize: 19.33 MB 	Instructions
	Linux x64 RPM * filesize: 18.79 MB 	Instructions
* Please use the 32-bit version for Java applet and Java Web Start support.

---

### Post by Paqman on 2009-10-15
The first place you should look for Linux software is in the package manager.

A good package to install that includes Java, Flash and multimedia codecs is ubuntu-restricted-extras. If you don't already have it, go to Applications > Add/Remove OR System > Admin > Synaptic and install it.

---

### Post by falconindy on 2009-10-15
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

If you envision yourself doing Java coding at some point, you can install the sun-java6-jre package as well.

---

### Post by mjp29 on 2009-10-15
> **Paqman said:**
> The first place you should look for Linux software is in the package manager.

A good package to install that includes Java, Flash and multimedia codecs is ubuntu-restricted-extras. If you don't already have it, go to Applications > Add/Remove OR System > Admin > Synaptic and install it.

ok I installed ubuntu-restricted-extras but get the same results

To offer more information to solicit more help:  I am at Adrive.com and get to the screen where I click upload folders (to be backed up online) and Adrive.com gives me the message below and I quote


"Tips:

    * This upload tool requires Java. If the upload tool is not visible, please make sure your browser has Java enabled or download Java
    * To upload a directory, simply drag and drop your selected directory onto the applet to add it to your upload list. You can also click the 'Add' button to browse your files and folders.
    * The selected directory or folder content will appear in your upload list, also indicating the location of the files. Example: "foo/bar.txt" the file "bar.txt" will be uploaded to the folder "foo" in the current server directory. If you haven't already created that directory on the server, this tool will create it for you.
    * Some virus protection software "proxies" the connection and will show the upload as 100% complete even though the proxy is still sending the data to the server. Please be patient and let it run. It will refresh upon completion."

Further information:  I can use youtube.com and view videos (does that use Java?).  What other website could I go to and see if I truly don't have Java installed or enabled - ?

---

### Post by Paqman on 2009-10-15
> **mjp29 said:**
> What other website could I go to and see if I truly don't have Java installed or enabled - ?

[This one]("http://java.com/en/download/installed.jsp?detect=jre&try=1")

Does adrive.com have a "browser uploader" available, or do you have to use the Java version?

---

### Post by niteshifter on 2009-10-15
> **mjp29 said:**
> ... What other website could I go to and see if I truly don't have Java installed or enabled - ?

Assuming Firefox:

In the address bar type:
```
about:plugins
```
and press enter. If you've Java plugins they'll show up here.

PS. Youtube isn't Java-driven, it uses Flash.

---

### Post by jeremyswalker on 2009-10-15
I looked at the dependencies of ubuntu-restricted-extras and couldn't find Java listed as a dependency. So, you need to install Java.
```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by mocoloco on 2009-10-15
[Install java via your package manager]("apt:sun-java6-jre,sun-java6-plugin,sun-java6-fonts").  If you're asked what to use to open the link select "apturl" and make it the default.  Why don't more people use apturl ;)

---

