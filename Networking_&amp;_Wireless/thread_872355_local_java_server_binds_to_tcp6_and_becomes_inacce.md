---
title: "local java server binds to tcp6 and becomes inaccessible"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by tux_attack on 2008-07-27
I have been trying to run [Pandora's Jar]("http://hak5.org/forums/index.php?showtopic=983"), a .jar file which as part of it's function starts a local web server (default port 8085). The first time I ran it it ran fine but the second time the java widow loaded a 0 by 0 pixel unresizeable output window that was just window decoration.  Console output said it started fine but when I tried loading the control webpage in firefox I got this error:
```
HTTP/1.0 404 Not Found Date: Sun Jul 27 17:49:18 MDT 2008 
Content-Type: text/html Cache-Control: no-cache, no-store, must-revalidate, max-age=-1 
server.Server: Pandora's Jar Connection: close  file not found
```I then ran netstat -an and learned that it was listening on tcp6 instead of tcp
```
tcp6       0      0 :::8085                 :::*                    LISTEN
```Does any one know what might be causing the webpage inacessability?

PS: I tried the page in seamonkey too, so I know it's not an extension issue.

---

### Post by tinny on 2008-07-28
Can you run the *.jar file from the command line?

Something like...
```

java pandora.jar

```

And post back any output. Ive read that this application is windows only... but keep trying you never know...

What happens if you restart your machine? The first instance of pandora may not be releasing that port.

---

### Post by tux_attack on 2008-07-28
Yes I can run it, the command I usually use is ```
java -jar pandora.jar 8085
``` I get the same command line output running it now that I got when it was working except for the socket exception.

Here's the output after a restart, it's two incidences. Seamonkey crashed loading the first time but that is an issue not related to the page. (probably bad ram)
```
sean@seamless-pownage:~$ java -jar /home/sean/Pandora/pandora.jar 8085
INFO [main] (Client.java:32) - initing app
 INFO [Thread-1] (Server.java:55) - running
 INFO [Thread-1] (Server.java:42) - Welcome to Pandora's Jar

 INFO [Thread-1] (Server.java:42) - Attempting to lauch on port 8085...
 INFO [Thread-1] (Server.java:42) - OK!

 INFO [Thread-1] (Server.java:42) - [ready, lets grab some MP3's!!!]


 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET / HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:110) - processing static request. path: GET / HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:112) - path =
DEBUG [Thread-1] (ProcessAction.java:116) - using path: pandoraGrabber.html
 INFO [Thread-1] (ProcessAction.java:126) - documentType = HTML
 INFO [Thread-1] (ProcessAction.java:128) - fileType = HTML

#here is about where seamonkey crashed and probably caused the broken pipe

INFO [Thread-1] (Server.java:42) - Broken pipe
java.net.SocketException: Broken pipe
        at java.net.SocketOutputStream.socketWrite0(Native Method)
        at java.net.SocketOutputStream.socketWrite(SocketOutputStream.java:92)
        at java.net.SocketOutputStream.write(SocketOutputStream.java:115)
        at java.io.DataOutputStream.writeBytes(DataOutputStream.java:259)
        at servlet.ProcessAction.handleStaticRequest(ProcessAction.java:136)
        at server.Server.handleHTTPRequest(Server.java:155)
        at server.Server.run(Server.java:83)

#complete seamonkey request
  
INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET / HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:110) - processing static request. path: GET / HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:112) - path =
DEBUG [Thread-1] (ProcessAction.java:116) - using path: pandoraGrabber.html
 INFO [Thread-1] (ProcessAction.java:126) - documentType = HTML
 INFO [Thread-1] (ProcessAction.java:128) - fileType = HTML

#java closed with a control-c

sean@seamless-pownage:~$ java -jar /home/sean/Pandora/pandora.jar 8085
 INFO [main] (Client.java:32) - initing app
 INFO [Thread-1] (Server.java:55) - running
 INFO [Thread-1] (Server.java:42) - Welcome to Pandora's Jar

 INFO [Thread-1] (Server.java:42) - Attempting to lauch on port 8085...
 INFO [Thread-1] (Server.java:42) - OK!
 INFO [Thread-1] (Server.java:42) - [ready, lets grab some MP3's!!!]
 INFO [Thread-1] (Server.java:42) - localhost connected to server.
 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET / HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:110) - processing static request. path: GET / HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:112) - path =
DEBUG [Thread-1] (ProcessAction.java:116) - using path: pandoraGrabber.html
 INFO [Thread-1] (ProcessAction.java:126) - documentType = HTML
 INFO [Thread-1] (ProcessAction.java:128) - fileType = HTML

#another complete seamonkey request
```This is just the .jar's output though; I haven't run it in verbose java yet.
As for compatibility, I have loaded the page and .jar successfully the first time I ran it (today) so I know it is compatible.

---

### Post by tinny on 2008-07-28
Nice name, spelled right too! ;)

Have you tried the classic Windows fix? Reboot!

---

### Post by tinny on 2008-07-28
What JRE are you using?

```

java -version

```

Hope its not the GNU JRE...

Are you viewing the Pandora URL with SeaMonkey??? Have you tried another browser? FireFox? Or maybe even Explorer on Windows?

---

### Post by tux_attack on 2008-07-28
```
sean@seamless-pownage:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```

The  problem has persisted on two reboots so far. Also I can acess pandora.com just fine, the way the app works is by loading Pandora in an iframe then acting as a wrapper of sorts to allow for streamripping, last.fm logging, etc. The issue is that the page wont even load properly.

I have tried Seamonkey, Firefox and Opera all with the same error. The issue seems to be a server issue, not a client one from the wireshark data.

Here's the TCP stream of the connection in wireshark, seamonkey makes a get request with headers. All the the server says back is it's http version and 200 which means ok.
```
GET / HTTP/1.1
Host: localhost:8085
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.13) Gecko/20080313 SeaMonkey/1.1.9 (Ubuntu-1.1.9+nobinonly-0ubuntu1)
Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Cache-Control: max-age=0

HTTP/1.0 200
```

I atached the wireshark capture as a .txt so it could be uploaded, it would need to be opened by wireshark to be comprehensible, a text editor won't work.

---

### Post by tinny on 2008-07-28
The pandora.jar that ive read about is a small servlet container (something like jetty) that gets deployed on your local machine. You then browse to this from a local web browser (http://localhost:<whatever port>)

In my experience the "broken pipe" socket exception is an error in the applications code (some sort of streaming problem).

I am interest to try this application out. Can you attach the jar? Or post a link?

Is this it? [http://sourceforge.net/projects/pandoras-jar/](http://sourceforge.net/projects/pandoras-jar/) if so its open source, have a crack at fixing it :)

---

### Post by mr53308 on 2008-07-29
Hey there, your problem has nothing to do with Java, strictly with the default installation of Ubuntu with IP v6 enabled

I know because I had the same problem, only it was some portforwarding I was setting up with an SSH session locally.

If you look at your NIC with 'ifconfig -a' you'll find you have not only a ipv4 address but an ipv6 one as well.

To fix this:
Change the line is /etc/modprobe.d/aliases from:

    alias net-pf-10 ipv6

to

    alias net-pf-10 off

Then, I rebooted and presto, no ipv6 enabled or configured anymore.

---

### Post by tux_attack on 2008-07-29
I tried disabling ipv6 and after the reboot Pandora's Jar listened on tcp instead of tcp6 but it still gave me the same error so I guess it's something with the application. Thanks though :-)

Tinny, the project was at source forge for a while but the [latest release is here]("http://hak5.org/forums/index.php?showtopic=7413"). With source code in the src directory of the .zip. Some other people have been trying to get it to work on linux as well so I'm looking through those threads.

EDIT:

Full java source code is in the src directory of the .zip available at the link above.


The window specified by src/Client/Client.java defined at lines 42-65 never gets fully drawn (see image) so something breaks before line 65 

The server is specified in src/Server/Server.jar and I know it gets to at least line 106 with line 105 returning null```

105:String action = request.getParamter(Constants.PARAM_ACTION); 
106:LOG.debug("processing request with action: " + action);
```

---

### Post by tux_attack on 2008-08-04
Could anyone help me with debugging this?

---

### Post by tinny on 2008-08-08
I am unable to use the Pandora service in my area (New Zealand) due to licensing constraints . See attached "Screenshot.png".

So unfortunately I wont be much help to you.

However I have run the application and I dont get any problems. (this may just be because I cant use the pandora service)

```

sean@sean-eee:~/development/testWorkspace/Pandora$ sudo java -jar pandora.jar 8085
 INFO [main] (Client.java:32) - initing app
 INFO [Thread-1] (Server.java:55) - running 
 INFO [Thread-1] (Server.java:42) - Welcome to Pandora's Jar - darkone_05 edition

 INFO [Thread-1] (Server.java:42) - Attempting to lauch on port 8085...
 INFO [Thread-1] (Server.java:42) - OK!

 INFO [Thread-1] (Server.java:42) - [ready, lets grab some MP3's!!!]


 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET / HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET / HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = 
DEBUG [Thread-1] (ProcessAction.java:127) - using path: pandoraGrabber.html
 INFO [Thread-1] (ProcessAction.java:137) - documentType = HTML
 INFO [Thread-1] (ProcessAction.java:139) - fileType = HTML
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /js/prototype-1.4.0.js HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /js/prototype-1.4.0.js HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = js/prototype-1.4.0.js
DEBUG [Thread-1] (ProcessAction.java:127) - using path: js/prototype-1.4.0.js
 INFO [Thread-1] (ProcessAction.java:137) - documentType = JS
 INFO [Thread-1] (ProcessAction.java:139) - fileType = JS
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /js/pandoraGrabber.js HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /js/pandoraGrabber.js HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = js/pandoraGrabber.js
DEBUG [Thread-1] (ProcessAction.java:127) - using path: js/pandoraGrabber.js
 INFO [Thread-1] (ProcessAction.java:137) - documentType = JS
 INFO [Thread-1] (ProcessAction.java:139) - fileType = JS
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/css/pandorajar.css HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/css/pandorajar.css HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/css/pandorajar.css
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/css/pandorajar.css
 INFO [Thread-1] (ProcessAction.java:137) - documentType = CSS
 INFO [Thread-1] (ProcessAction.java:139) - fileType = CSS
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /js/pandora.js HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /js/pandora.js HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = js/pandora.js
DEBUG [Thread-1] (ProcessAction.java:127) - using path: js/pandora.js
 INFO [Thread-1] (ProcessAction.java:137) - documentType = JS
 INFO [Thread-1] (ProcessAction.java:139) - fileType = JS
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/north.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/north.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/north.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/north.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/east.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/east.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/east.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/east.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/south.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/south.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/south.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/south.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/west.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/west.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/west.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/west.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/ne.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/ne.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/ne.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/ne.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/se.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/se.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/se.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/se.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/sw.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/sw.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/sw.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/sw.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /process?action=version&_= HTTP/1.1
DEBUG [Thread-1] (Server.java:170) - params found: 2
DEBUG [Thread-1] (Server.java:183) - adding param: [name: action value: version]
DEBUG [Thread-1] (Server.java:106) - processing request with action: version
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/octopus/nw.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/octopus/nw.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/octopus/nw.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/octopus/nw.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/fond.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/fond.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/fond.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/fond.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/sup.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/sup.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/sup.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/sup.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/inf.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/inf.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/inf.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/inf.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/d.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/d.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/d.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/d.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/g.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/g.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/g.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/g.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/coininfg.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/coininfg.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/coininfg.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/coininfg.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/coininfd.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/coininfd.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/coininfd.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/coininfd.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/coinsupd.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/coinsupd.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/coinsupd.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/coinsupd.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/aqua/coinsupg.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/aqua/coinsupg.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/aqua/coinsupg.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/aqua/coinsupg.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/idpanel.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/idpanel.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/idpanel.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/idpanel.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/grabit.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/grabit.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/grabit.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/grabit.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/top.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/top.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/top.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/top.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /skins/blended/images/bottom.gif HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /skins/blended/images/bottom.gif HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = skins/blended/images/bottom.gif
DEBUG [Thread-1] (ProcessAction.java:127) - using path: skins/blended/images/bottom.gif
 INFO [Thread-1] (ProcessAction.java:137) - documentType = GIF
 INFO [Thread-1] (ProcessAction.java:139) - fileType = GIF
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /favicon.ico HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /favicon.ico HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = favicon.ico
DEBUG [Thread-1] (ProcessAction.java:127) - using path: favicon.ico
 INFO [Thread-1] (ProcessAction.java:137) - documentType = ICO
 INFO [Thread-1] (ProcessAction.java:139) - fileType = ICO
 INFO [Thread-1] (Server.java:42) - localhost connected to server.

 INFO [Thread-1] (Server.java:101) - handling request
 INFO [Thread-1] (Server.java:102) - processing url: GET /favicon.ico HTTP/1.1
DEBUG [Thread-1] (Server.java:106) - processing request with action: null
 INFO [Thread-1] (ProcessAction.java:121) - processing static request. path: GET /favicon.ico HTTP/1.1
 INFO [Thread-1] (ProcessAction.java:123) - path = favicon.ico
DEBUG [Thread-1] (ProcessAction.java:127) - using path: favicon.ico
 INFO [Thread-1] (ProcessAction.java:137) - documentType = ICO
 INFO [Thread-1] (ProcessAction.java:139) - fileType = ICO

```

Question have you run pandora.jar as sudo?

```

sudo java -jar pandora.jar

```

This is how I ran it.

Also if running as sudo doesnt work you could try adding the following line of code to ProcessAction.java line 141

[PHP]
line 140: output.writeBytes(Util.writeResponseHeader(ReturnCodes.OK, fileType, null));
line 141: output.flush();
[/PHP]

---

### Post by tux_attack on 2008-08-11
I doubt that not being able to access pandora causes it to work, at least I know that it can run on Hardy and isn't a fundamental issue with the distro. I might try to debug it and see where it is breaking. If I do I'll post what I get.

Edit: What would be the easiest way to open the src directory as a compilable project?
Edit: Got it, now I just adding the dependent classes.

         Thanks!

---

### Post by tinny on 2008-08-11
> **tux_attack said:**
> I doubt that not being able to access pandora causes it to work, at least I know that it can run on Hardy and isn't a fundamental issue with the distro. I might try to debug it and see where it is breaking. If I do I'll post what I get.

Edit: What would be the easiest way to open the src directory as a compilable project?

         Thanks!

Yeah, its really hard for me to tell whats going on without being able to do a full end to end type test.

PM me your email address and ill send you the Eclipse project that I put together.

---

### Post by tux_attack on 2008-08-14
I got the project and loaded it into eclipse fine now it gives me 90+ errors most stemming from  unresolvable classes or imports. The first error is

attributes cannot be resolved    Pandora/src/server    Session.java    line 16

```
package server; 
 
import java.util.Map; 
import java.util.HashMap; 
 
public class Session { 
    private Map<String,Object> attributes; 
    private String sessionId; 
 
    public Session(String sessionId) { 
        this.sessionId = sessionId; 
        this.attributes = new HashMap<String, Object>(); 
    } 
 
    public void setAttribute(String attributeName, Object attributeValue) { 
        **attributes**.put(attributeName, attributeValue);
```
I tried various mixes of java, firefox and wine. I found that with the jar running under WINE the output window fully loaded but the server still gave the same error with both native and WINE firefox.

Also, it seems that the error occurs at an early point in the request since it's a 404. So I don't believe being unable to use Pandora would affect the execution of the request. The jar only interacts with the Pandora tuner after the page is loaded.

---

### Post by tinny on 2008-08-15
So do you still have these errors in the project?

There is a "lib" folder that has a whole lot of jar files that are dependencies for the project. Make sure that those jar are imported as libs for the project (should be).

---

