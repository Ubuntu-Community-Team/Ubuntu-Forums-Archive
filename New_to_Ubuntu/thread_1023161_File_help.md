---
title: "File help"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by nightfall47 on 2008-12-27
Hello, I'm fairly new to linux. There's a java (I believe) game at [http://www.piettes.com/fallingsandgame/download.html]("http://www.piettes.com/fallingsandgame/download.html") called 'wxSand'. I've downloaded the linux version of it, but I'm having trouble running it. In 'Properties' on the file, it's Type is "Type: executable (application/x-executable)". I open terminal and type the following:

[B]cd Desktop
sh ./fsg-4.4[/B]

Then, it responds with this:

./fsg-4.4: 4: d&#65533;N&#65533;?&#65533;&#65533;&#65533;jD&#65533;&#65533;&#65533;01&#65533;&#65533;&#330;}r: not found
./fsg-4.4: 4: ELF4&#65533;.4 	(44&#65533;4&#65533;  TT&#65533;T&#65533;&#65533;&#65533;&#65533;B-&#65533;B-&#65533;B-&#65533;&#65533;&#65533;&#65533;T&#65533;&#65533;8E-&#65533;&#65533;&#65533;&#65533;hh&#65533;h&#65533;  P&#65533;td&#65533;&#65533;&&#65533;r&#65533;r\&#65533;\&#65533;Q&#65533;td&#65533;e(/lib/ld-linux.so.2GNU	&#65533;Z&#65533;&#65533;&#65533;&#65533;F&#65533;)oo/&#65533;&#65533;&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;J
S&#65533;@&#65533;&#65533;a&#65533;&#65533;&#65533;&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;r=&#65533;&#65533;\,&#65533;-o&#65533;&#65533;&#65533;J
           W&#65533;&#65533;9&#65533;D&#65533;&#65533;&#65533;&#65533;&#65533;m&#65533;&#65533;&#65533;:&#65533;	&#65533;&#65533;Lw%&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;KV&#65533;P&#65533;&#65533;&#65533;C
 l&#65533;&#65533;;,\&#65533;&#65533;&#65533;g<&#65533;&#65533;&#65533;&#65533;&#65533;.&#65533;sB~M&#65533;&#65533;&#65533;&#65533;x5&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;	&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;!f(&#65533;&#65533;&#65533;wkC&#65533;T&#65533;&#65533;&#65533;2&#65533;&#65533;_&#65533;&#65533;h
&#65533;&#65533;&#65533;&#65533;8&#65533;&#65533;E&#65533;&#65533;W&#65533;i&#65533;&#65533;&#65533;|&#65533;E&#65533;O&#65533;B3&#65533;y-&#65533; &#65533;&#65533;`&#65533;&#65533;u&#65533;_&#65533;G&#65533;?&#65533;<#&#65533;Q&#65533;&#65533;&#65533;{&#65533;&#65533;o&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;	&#65533;i.&#65533;&#65533;)&#65533;F&#65533;#&#65533;&#65533;z$&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t[&#65533;&#65533;K&#65533;9&#65533;A@
                                                                @y&#65533;&#65533;&#65533;|*&#65533;p&#65533;&#65533;&#65533;h&#65533;v&#65533;PQ&#65533;&#65533;>&#65533;
                              &#65533;f4Ejw&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;b&#65533;8&#65533;eBR&#65533;&#65533;&#65533;&#65533;n&#65533;]&#65533;9&#65533;&#65533;&#65533;&#65533;d1U8vhv&#65533;&#65533;&#65533;7&#65533;I: not found
./fsg-4.4: 5: Syntax error: ")" unexpected

Yes, that is precisely what it is replying with. Is there something I'm doing wrong? Is the file itself corrupt? Perhaps it's incompatible with Ubuntu 8.10, I'm not able to determine this, though. I'd appreciate any help. Thanks

---

### Post by aheckler on 2008-12-27
You need to do:

```
cd ./Desktop
java -jar ./fsg-4.4.jar
```

---

### Post by nightfall47 on 2008-12-27
Ok, I tried that and now it says:

q1@home:~/Desktop$ java -jar ./fsg-4.4.jar
Exception in thread "main" java.util.zip.ZipException: ./fsg-4.4.jar
   at java.util.zip.ZipFile.openFile(ZipFile.java:122)
   at java.util.zip.ZipFile.<init>(ZipFile.java:137)
   at java.util.jar.JarFile.<init>(JarFile.java:199)
   at java.util.jar.JarFile.<init>(JarFile.java:181)
Caused by: java.io.FileNotFoundException: ./fsg-4.4.jar
   at java.io.RandomAccessFile.<init>(RandomAccessFile.java:135)
   at java.io.RandomAccessFile.<init>(RandomAccessFile.java:172)
   at java.util.zip.ZipFile.openFile(ZipFile.java:117)
   ...3 more
Caused by: java.io.IOException: No such file or directory
   at gnu.java.nio.VMChannel.open(Native Method)
   at gnu.java.nio.VMChannel.openFile(VMChannel.java:530)
   at gnu.java.nio.FileChannelImpl.<init>(FileChannelImpl.java:151)
   at gnu.java.nio.FileChannelImpl.create(FileChannelImpl.java:141)
   at java.io.RandomAccessFile.<init>(RandomAccessFile.java:127)
   ...5 more

---

### Post by nightfall47 on 2008-12-27
I think a bit of stupidity on my part is what gave me the above ^ crap. I just installed sun-java6-bin and a few others in synaptic and now when I try to open fsg-4.4 it gives me:
Unable to access jarfile ./fsg-4.4.jar

---

### Post by nightfall47 on 2008-12-27
Anyone have an idea?

---

### Post by snova on 2008-12-27
It's not a script, and it's not a .jar file. Just run it. Make sure it is executable first (from Permissions).

If it doesn't work, try running it from a terminal and show us the error.

---

### Post by nightfall47 on 2008-12-28
Alright, when I try running it after making it executable it says this:

q1@home:~/Desktop$ ./fsg-4.4
./fsg-4.4: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

and if I try 'sh ./fsg-4.4' it gives me the huge error message I posted in the first post.

---

### Post by snova on 2008-12-28
> **nightfall47 said:**
> q1@home:~/Desktop$ ./fsg-4.4
./fsg-4.4: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

That'll do. Lets try this and hope it works:

```
cd /usr/local/lib
sudo ln -s /usr/lib/libexpat.so.1 libexpat.so.0
```

Try running it again from the terminal.

This is assuming the two libraries are binary compatible. I'm not hopeful.

If this fails, I still have one more idea! A much more likely one...

---

