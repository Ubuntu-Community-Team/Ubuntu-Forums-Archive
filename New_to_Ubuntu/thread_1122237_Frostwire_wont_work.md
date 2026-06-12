---
title: "Frostwire wont work"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by tropdoug on 2009-04-10
Hi guys

I am reinstalling programs I used to use on 8.10 (now have the new jaunty installed) 

one of them is Frostwire but when I try to start it from the terminal this is what I get returned

Starting FrostWire...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/lib/jre1.6.0_13/bin/
Suitable java version found  [/usr/lib/jre1.6.0_13/bin/java = 1.6.0_13]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar

/usr/lib/jre1.6.0_13/bin/
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
**[COLOR=Blue]/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found[/COLOR]**

Obviously the line 158 needs to be altered in the frostwire.sh but I don't know what to.

I created a sym link to the Java exec which is working, and yet frostwire wont use it. 

(my Java is on usr/local/Java so the sym link to that is in usr/lib)

Any ideas would be greatly appreciated

---

### Post by oldos2er on 2009-04-10
Run
```
sudo update-alternatives –config java
```
and point it to your /usr/lib/jre1.6.0_13/bin/java directory.

---

### Post by tropdoug on 2009-04-11
hmmm .......... just says "no alternative to Java"

---

### Post by taurus on 2009-04-11
What are the outputs of these commands?

```
java -version
ls -la /usr/local/java
```

---

### Post by tropdoug on 2009-04-12
Here is the output. The first one is a bit odd because java is installed as you can see from the second. Firefox works perfectly too. 

I am wondering however if this is the first problem. A bit higher up in the return from my command 'frostwire' in the terminal was this 

```
sh: unpack200: not found
```I have investigated and found that particular file in /usr/lib/frostwire and it is a text file. It says 
```

''' 
This script will run everytime frostwire is launched. It'll check if there are 
any .pack files the frostwire installation folder. It'll unpack them and then 
it'll update the hashes file, so that frostwire can start. 
''' 
import os 
INSTDIR='/usr/lib/frostwire'     
def makeHashes(): 
  #creates the hashes based on the md5s of all the jars 
  import md5 
 
  #Get the path to the installation dir 
  #and work inside it 
  os.chdir(INSTDIR) 
  localFiles = os.listdir(".") 
 
  output = file('hashes','w') 
 
  for f in localFiles: 
    if f.endswith('.jar'): 
      fp = file(f,'rb') 
      line = f + "=" + str(md5.new(fp.read()).hexdigest()).upper() 
      fp.close() 
      output.write(line + "\n") 
      print line 
 
  output.close() 
 
def thereArePacks(): 
  os.chdir(INSTDIR) 
  packsFound = 0 
 
  for f in os.listdir(INSTDIR): 
    if f.endswith('.pack'): 
      packsFound += 1 
      break 
 
  return packsFound > 0 
 
def unpack200(): 
  os.chdir(INSTDIR) 
   
  for f in os.listdir(INSTDIR): 
    if f.endswith('.pack'): 
      file_name_no_ext = f[0:f.find('.pack')] 
      unpack_cmd = 'unpack200 --quiet %s %s' % (f, 
                                                file_name_no_ext + '.jar') 
 
      os.system(unpack_cmd) 
 
      #remove the pack, if and only if the equivalent .jar exists 
      if os.path.exists(file_name_no_ext + '.jar'): 
        os.remove(f) 
 
if __name__ == "__main__":       
    if thereArePacks(): 
      unpack200() 
      makeHashes() 
```

I also noticed that md5 is now deprecated (see below)

[COLOR=Blue]```
/usr/lib/frostwire/unpack200.py:10: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
```[/COLOR]```


HOSTNAME IS desktop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/lib/jre1.6.0_13/bin/
Suitable java version found  [/usr/lib/jre1.6.0_13/bin/java = 1.6.0_13]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar

/usr/lib/jre1.6.0_13/bin/
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found

douglas@desktop:~$ 
```

So maybe it's not to do with java, but more to do with unpack200 and or the need to use 'hashlib' (but how do I do that?)

**All input gratefully received!**

```
douglas@desktop:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * cacao-oj6-jre-headless
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
douglas@desktop:~$ 

```
```
douglas@desktop:~$ ls -la /usr/local/Java
total 19720
drwxr-xr-x  3 douglas root        4096 2009-04-11 09:17 .
drwxrwxr-x 14 douglas douglas     4096 2009-04-11 20:53 ..
drwxr-xr-x  8 douglas douglas     4096 2009-04-11 09:17 jre1.6.0_13
-rwxr-xr-x  1 douglas douglas 20177482 2009-04-11 07:54 jre-6u13-linux-i586.bin

```

---

### Post by clive littlewood on 2009-04-12
Hi

I had the same problem.

Just went to synaptic and searched for java.

Installed java 6 from there and frostwire works great !!!!!   :p


Clive

---

### Post by taurus on 2009-04-12
```
ls -la /usr/local/Java/jre1.6.0_13/bin
```

---

### Post by tropdoug on 2009-04-13
Taurus 
```

douglas@desktop:~$ sudo ls -la /usr/java/jre1.6.0_13/bin
total 748
drwxr-xr-x 2 root root   4096 2009-03-09 21:37 .
drwxr-xr-x 8 root root   4096 2009-04-13 11:14 ..
lrwxrwxrwx 1 root root     10 2009-04-13 11:14 ControlPanel -> ./jcontrol
-rwxr-xr-x 1 root root  47308 2009-03-09 19:53 java
-rwxr-xr-x 1 root root  25634 2009-03-09 19:55 java_vm
-rwxr-xr-x 1 root root  83856 2009-03-09 19:55 javaws
-rwxr-xr-x 1 root root   6347 2009-03-09 19:55 jcontrol
-rwxr-xr-x 1 root root  47447 2009-03-09 19:53 keytool
-rwxr-xr-x 1 root root  47679 2009-03-09 19:53 orbd
-rwxr-xr-x 1 root root  47515 2009-03-09 19:53 pack200
-rwxr-xr-x 1 root root  47807 2009-03-09 19:53 policytool
-rwxr-xr-x 1 root root  47447 2009-03-09 19:53 rmid
-rwxr-xr-x 1 root root  47447 2009-03-09 19:53 rmiregistry
-rwxr-xr-x 1 root root  47475 2009-03-09 19:53 servertool
-rwxr-xr-x 1 root root  47679 2009-03-09 19:53 tnameserv
[COLOR=Blue]-rwxr-xr-x 1 root root 189274 2009-03-09 19:53 unpack200[/COLOR]

douglas@desktop:~$ 
```

The problem is not java its the unpack200 file that frostwire is looking for and cannot find. I can see it right there in the java directory. 

```

douglas@desktop:~$ sudo frostwire
**[COLOR=Blue]sh: unpack200: not found[/COLOR]**
/usr/lib/frostwire/unpack200.py:10: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
HOSTNAME IS desktop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
**[COLOR=Blue]Java exec found in  /usr/java/jre1.6.0_13/bin/[/COLOR]**
Suitable java version found  [/usr/java/jre1.6.0_13/bin/java = 1.6.0_13]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
**[COLOR=Blue]Unable to access jarfile FrostWire.jar[/COLOR]**
```

I have highlighted the three areas that seem to me to be the problem. Not sure if I am right,. but I hope that you or someone else can suggest a fix.

---

### Post by tropdoug on 2009-04-16
Solved, found a thread saying that Limewire now worked with Linux, and they were right. installed like a dream, and works perfectly. 

[http://www.limewire.com/download/version.php](http://www.limewire.com/download/version.php)

---

### Post by MommaMiss on 2009-04-17
You guys are all going to think I am pathetic but I have downloadd frostwire, ran the package installer and nothing happened after that what am I doing wrong?
(I have only been using ubuntu for about ten hours so please use little words *s*)

---

### Post by taurus on 2009-04-17
> **MommaMiss said:**
> You guys are all going to think I am pathetic but I have downloadd frostwire, ran the package installer and nothing happened after that what am I doing wrong?
(I have only been using ubuntu for about ten hours so please use little words *s*)

Look in Applications -> Internet.

---

### Post by tropdoug on 2009-04-17
Hi Momma Miss

welcome to the wrold of Linux - it takes a little learning but the rewards are well worth it. 

Ok - sounds like you may have the same issue I did, but the first thing is to find out whether you have Java instaled and running

go to [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

and about a third of a way down the page you will see a revolving circle - that is a script that is looking for java on your computer. If it finds it, it will display the version and vendor number. You should be using the one from this link for your system

[http://www.java.com/en/download/manual.jsp#lin](http://www.java.com/en/download/manual.jsp#lin) (by the way what version of linux are you using?)

There are installation instructions also from the download link. They are not that complicated, but if you get stuck, come back here. 

Once installed and you have restarted your browser (I use Firefox) in the address bar type [COLOR=Blue]'about:plugins'[/COLOR] that will bring up a list of the plugiuns that your browser is using and should include the Java version you just installed.

With frostwire I used it on all my previous Ubuntu Versions, but this thread shows you that when I changed over to the new Jaunty Jackalope version Frostwire would not load, which sounds like what is happening to you. So after continuing to research elswhere I came upon a thread that told me that Limewire (open source) worked prefectly, and it did. 

My suggestion would be to try Limewire and see what happens 

[http://www.linux23.com/download/limewire-pro-5-1-2-multilanguage-linux:4c458eefc8448e7d458ea960a2d96b37689ef7f1](http://www.linux23.com/download/limewire-pro-5-1-2-multilanguage-linux:4c458eefc8448e7d458ea960a2d96b37689ef7f1)

---

