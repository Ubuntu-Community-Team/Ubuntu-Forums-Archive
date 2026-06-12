---
title: "Cxfreeze won't compile anything."
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Manaan on 2010-06-03
I'm trying to compile a simple hello world python script with cxfreeze. When I run [FONT=Courier New]cxfreeze test.py[/FONT] I get:
```
creating directory /home/ross/Downloads/dist
copying /usr/lib/pymodules/python2.6/cx_Freeze/bases/Console -> /home/ross/Downloads/dist/test
copying /usr/lib/libpython2.6.so.1.0 -> /home/ross/Downloads/dist/libpython2.6.so.1.0
Traceback (most recent call last):
  File "/usr/bin/cxfreeze", line 5, in <module>
    main()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/main.py", line 170, in main
    freezer.Freeze()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 405, in Freeze
    self._FreezeExecutable(executable)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 173, in _FreezeExecutable
    exe.copyDependentFiles, scriptModule)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 333, in _WriteModules
    initModule = finder.IncludeFile(initScript, "cx_Freeze__init__")
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 386, in IncludeFile
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 259, in _LoadModule
    module.code = compile(fp.read() + "\n", path, "exec")
TypeError: compile() expected string without null bytes
```

I have very little Linux experience so please keep responses simple.

---

### Post by cmcqueen1975 on 2010-07-04
Yes I'm having the same trouble. It's not your fault, but probably a bug in the cx-freeze package in Ubuntu.

I haven't investigated to see what might be the issue. It would be worth posting something to the cx_Freeze mailing list to see what anyone can say there.

[https://lists.sourceforge.net/lists/listinfo/cx-freeze-users](https://lists.sourceforge.net/lists/listinfo/cx-freeze-users)

---

### Post by cmcqueen1975 on 2010-07-04
I ended up downloading and installing the latest version (4.1.2) from source code.

First, download the source code from the cx_Freeze web site.

Unpack it with:
```
tar zxf cx_Freeze-4.1.2.tar.gz
```

Then cd into the dir:
```
cd cx_Freeze-4.1.2/
```

Then build and install:
```
sudo python setup.py install
```

It might well give you an error about a missing ssl library. If so:
```
sudo apt-get install libssl-dev
```
then try the previous build and install step again.

---

### Post by PerryTatchett on 2010-07-06
Hi all.

I also ran into this issue, but I found an extremely cheesy hack to fix this. The problem is that cxfreeze is opening all files with universal newline support on, and as such the following happens:

cx_Freeze opens a compiled bytecode file, and scans for the magic number, '\xd1\xf2\r\n', but universal newline mode turns this into '\xd1\xf2\n', thus misidentifying the bytecode as Python source, which is then passed to compile, which crashes.

When I hit this issue, in about twenty minutes I found a cheesy workaround, namely to insert:

```

        # TOTAL HACK WORKAROUND BY PETER
        if fp.name.endswith(".pyc"):
            print "Peter's horrible hack is activiating, forcing", fp.name, "into binary mode, and as compiled Python."
            type = imp.PY_COMPILED
            # Next, switch out of universal newline mode in this crazy case.
            fp.close()
            fp = open(fp.name, "rb")
        # END TOTAL HACK

```

... before line 258 of /usr/lib/pymodules/python2.6/cx_Freeze/finder.py

Or, as a patch:

```

*** tmp/orginal_finder.py	2010-07-06 13:33:14.000000000 -0400
--- /usr/share/pyshared/cx_Freeze/finder.py	2010-07-05 13:09:07.000000000 -0400
***************
*** 255,260 ****
--- 255,268 ----
          module = self._AddModule(name)
          module.file = path
          module.parent = parent
+         # TOTAL HACK WORKAROUND BY PETER
+         if fp.name.endswith(".pyc"):
+             print "Peter's horrible hack is activiating, forcing", fp.name, "into binary mode, and as compiled Python."
+             type = imp.PY_COMPILED
+             # Next, switch out of universal newline mode in this crazy case.
+             fp.close()
+             fp = open(fp.name, "rb")
+         # END TOTAL HACK
          if type == imp.PY_SOURCE:
              module.code = compile(fp.read() + "\n", path, "exec")
          elif type == imp.PY_COMPILED:

```

Hope this solves your problem,
Cheers.

-Peter Schmidt-Nielsen

---

### Post by cdated257 on 2010-07-11
Thanks @PerryTatchett, I was rather disappointed to see this error come up when I just wanted to do a simple test of cxfreeze on Lucid Lynx.  Your work around did the trick.

---

### Post by quangvhg on 2012-01-11
Thank @PerryTatchett for the fix, it works perfectly :)

---

