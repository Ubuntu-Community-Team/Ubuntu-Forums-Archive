---
title: "TuioToTouch Bridge doesn't work"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by webhackler on 2011-05-11
Hello Guys!

I was trying to use the tuiototouch bridge ([http://lii-enac.fr/en/architecture/linux-input/#tuiototouch](http://lii-enac.fr/en/architecture/linux-input/#tuiototouch)) to control Ubuntu with uTouch over the TUIO protocol.

I've already installed all the dependencies: pytuio ([http://code.google.com/p/pytuio/](http://code.google.com/p/pytuio/)) and uinput ([http://codegrove.org/projects/python-uinput](http://codegrove.org/projects/python-uinput)).

When I tried to run the tuiototouch script with (python tuiototouch.py) I got the following error:

```
georg@GeoTop:~/Desktop/tuiototouch$ python tuiototouch.py
Traceback (most recent call last):
  File "tuiototouch.py", line 20, in <module>
    import tuio
  File "/usr/local/lib/python2.6/dist-packages/tuio/__init__.py", line 91
    try:
       ^
IndentationError: unindent does not match any outer indentation level

```

I'm using Ubuntu 10.10 64bit, btw.

I hope someone can help me 

Greetings,
webhackler

---

### Post by Smart Viking on 2011-05-11
copy and paste from line 80 to 100 of that file into this forum, there is a syntax error.

---

### Post by webhackler on 2011-05-11
okay

File "/usr/local/lib/python2.6/dist-packages/tuio/__init__.py", line 91 :

```

    def get_helpers(self):
        """Returns a list of helper functions that provide access to the
        objects of each profile."""
        return list([profile.list_label for profile in self.profiles.values()])

    def update(self):
        """
        Tells the connection manager to receive the next 1024 byte of messages
        to analyze.
        """
 try:
         self.manager.handle(self.socket.recv(1024))
       except socket.error:
           pass

    def callback(self, *incoming):
        """
        Gets called by the CallbackManager if a new message was received 
        """
        message = incoming[0]
```

thx :)
Greetings
Webhackler

---

### Post by Smart Viking on 2011-05-11
In python, whitespace is very important, open the the file in a text editor and replace these lines:
 try:
         self.manager.handle(self.socket.recv(1024))
       except socket.error:
           pass

With this:
```

        try:
            self.manager.handle(self.socket.recv(1024))
        except socket.error:
            pass


```

---

### Post by webhackler on 2011-05-11
Well, that error has gone ... but a new one appeared :P

```
georg@GeoTop:~/Desktop/tuiototouch$ python ./tuiototouch.py
Traceback (most recent call last):
  File "./tuiototouch.py", line 131, in <module>
    tracking.update()
  File "/usr/local/lib/python2.6/dist-packages/tuio/__init__.py", line 92, in update
    self.manager.handle(self.socket.recv(1024))
AttributeError: 'Tracking' object has no attribute 'socket'

```

Greetings,
Webhackler

---

### Post by Smart Viking on 2011-05-11
Hm, either you're doing something wrong, or that specific version of the program that you've downloaded is not working. I don't have the time to read the program right now as it might take a long time, good luck. :)

---

### Post by webhackler on 2011-05-11
... hmm hopfully i find someone who can help me fixing this?

But thank you for helping :)

Greetings
Webhackler

---

