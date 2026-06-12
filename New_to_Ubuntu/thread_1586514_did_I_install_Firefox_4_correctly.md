---
title: "did I install Firefox 4 correctly?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by sallam on 2010-10-02
Greetings

I want to make sure that I didn't do it the wrong way. Here are the steps I made to install Firefox 4 beta 6:
[LIST=1]
[*]I downloaded the file from Firefox for linux
[*]I tried the software center, but it didn't work, so I right-clicked and selected "Extract Here"
[*]That gave me a folder named "firefox4" and inside it there is a folder named "firefox"
[*]Inside the firefox folder I clicked firefox.bin, but nothing happened, so I clicked firefox (shell script) and that started firefox
[*]I dragged the firefox shell script and dropped it in my panel
[/LIST]

Where those steps correct?
I mean, Firefox that came with ubuntu is located in /usr/lib
and there is another folder named firefox-3.6.10 located also in /usr/lib
and now my downloaded firefox 4 beta resides inside my Downloads folder, and I start it from there. Is that right? or should I move the extracted folder into /usr/lib or somewhere else you direct me to?

I'm worried because maybe when firefox gets an upgrade things get messy or fail to upgrade due to the non-default folder location?

(It works properly though, from where it is in the Downloads directory, using my settings, bookmarks and all, just like 3.6.10)

And I have another question please:
Is it shell scripts that start applications in ubuntu, similar to .exe in Windows? I'm confused because in my case the firefox-bin file says its 'executable' in the Type column.

Many thanks

---

### Post by gandaran on 2010-10-02
you can install it any where you like, just don't put it the other firefox directories, a more apropiate location would be /opt or /usr/local but I would keep it in the hidden home folder, just add o dot like .Firefox4 to the folder name.
> (It works properly though, from where it is in the Downloads directory, using my settings, bookmarks and all, just like 3.6.10)
are you sure its opening the real firefox4 and not firefox3? check the help » about mozilla firefox version, I believe you have to create a new firefox profile for firefox4 but I could be wrong here.

---

### Post by sallam on 2010-10-02
Yes, I double checked. It says Mozilla Firefox 4.0 Beta 6 both on top and in the about window.

---

### Post by Surkow on 2010-10-02
You have nothing to worry about. All things you did were correct. The only issue would be that the "firefox" alias (in the commandline for example) still links to your old Firefox version.

---

### Post by sallam on 2010-10-02
So if I use a command line I should state the full path to the firefox shell script, right? I did so while editing firefox in startup applications window, to delay its start for 20 sec., and it worked.

---

### Post by Surkow on 2010-10-02
Correct, or you can change the alias (which I wouldn't recommend if you still have the other firefox installed).

---

