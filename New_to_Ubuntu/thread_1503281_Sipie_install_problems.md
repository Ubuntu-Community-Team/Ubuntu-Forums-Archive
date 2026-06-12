---
title: "Sipie install problems"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by mcnever on 2010-06-06
Hi guys,
Need a little help getting Sipie running correctly. I'm using the install instructions below but once i get to the point of actually running sipie.py I enter my info and then i get this
 
everything appears to install ok... granted i'm a n00b and prolly wouldnt know if wasnt anyway though
 
[http://www.mythtv.org/wiki/Integrate_Sirius#Configuring_Sipie](http://www.mythtv.org/wiki/Integrate_Sirius#Configuring_Sipie)
 
```

root@myth-frontend:/usr/local/bin# sipie.py
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py:12: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Traceback (most recent call last):
  File "/usr/local/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1196144357', 'sipie.py')
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/EGG-INFO/scripts/sipie.py", line 22, in <module>
 
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 75, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 359, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 299, in tryGetStreams
Sipie.Factory.AuthError

```

---

### Post by mcnever on 2010-06-06
little update
 
just tried on another box and got the same results.  Both are running 9.10 with beautifulsoup 3.0.7 installed.  I did try it with the latest ver of beautifulsoup and got an expect parser error (known issue with sipie and that ver of soup i guess). 
 
I've looked around and it appears this happens occationally and clearing the ~/.sipie dir fixes it but i've tried that multiple times with no change.
 
any input would be greatly appreciated.
 
Thanks
Jason

---

### Post by mcnever on 2010-06-08
I redownloaded and easy_installed again, not sure if i had an old build before or not but it looks like the version number hasnt changed.  I am getting a different output now at least and its generating an Auth-ERROR.html file which just looks like its the sign-in page from sirius.  When i check the ~/.sipie/config the everything looks correct (the password is hashed now, was plain text before), i've also deleted and recreated the config multiple times.



```
/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py:12: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Login Error token not found:, see Auth-ERROR.html
Traceback (most recent call last):
  File "/usr/local/bin/cliSipie", line 8, in <module>
    load_entry_point('Sipie==0.1196144357', 'console_scripts', 'cliSipie')()
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 376, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 212, in auth
Sipie.Factory.LoginError

```


Jason

---

### Post by mcnever on 2010-06-08
Ok, so it looks like last November there were some changes on sirius's site and sipie was updated.  I dont know if those changes are 'applied' or posted on sourceforge.  or maybe i'm just pulling them down from the wrong place on sourceforge.  The build i'm looking at was last updated 10-3-2008.  I've found some updated files posted [here]("http://github.com/Kasuko/sipie/tree/master/Sipie/"). 
 
I'm just extracting the tar ball (damn BP) and using the updated files, but looks like there might be some problems with the python code.  below is the output.
 
```
Traceback (most recent call last):
  File "/usr/local/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1196144357', 'sipie.py')
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/EGG-INFO/scripts/sipie.py", line 6, in <module>
  File "build/bdist.linux-i686/egg/Sipie/__init__.py", line 12, in <module>
    # ;-)
  File "/usr/local/lib/python2.6/dist-packages/Sipie-0.1196144357-py2.6.egg/Sipie/Config.py", line 72
    return items
    ^

```
 
I'll keep pluggen a way at it.  BTW is anyone else out there, this thread feels like its just truning into a blog of my sipie problems.
 
Thanks
Jason

---

### Post by mcnever on 2010-06-08
SUCCESS!! sipie is actually working
 
It looks like the files on sf are old, pre november change.  I ended up pulling the files from [here]("http://github.com/johnrabotnik/sipie") and the easy_stall went easy.
 
after that ended up having some PulseAudio problems that i didnt see before because mythtv was using alsa.
 
still having some problems with sipie_myth and mythPlayer.py both are giving me "******FATAL: Invalid Stream!******' regardless of the channel name.  but i can start sipie directly from the command line using the channel name... humm....
 
Jason

---

