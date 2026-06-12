---
title: "Pida"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by smurfgod on 2009-01-07
i have python on my comp..like everyone else...and when i go to my programming tab and click PIDA it says that its starting and that it loves me...it never opens and i cant find it in my home folder.came someone help me find it...plz


smurf    :D

---

### Post by jken146 on 2009-01-08
Try typing ```
pida
``` in the terminal.  If the program does not start, what does ```
whereis pida
``` tell you?

---

### Post by lzlzlz on 2009-02-23
I have the same problem.

whereis pida gives:
pida: /usr/bin/pida /usr/lib/pida /usr/share/man/man1/pida.1.gz

When I start pida in terminal following happens:

1. Greetings from pida telling me that pida is in love,

2. Emacs starts with an error message in minubuffer: 

command-line-1: Unknown option `--parent-id' 

and the whole message buffer sayes:

("emacs" "--parent-id" "104857801" "-f" "server-start" "-l" "/home/lz/.pida2/pida_emacs_init.el")
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 00debian-vars...done
Loading /etc/emacs/site-start.d/50aribas.el (source)...done
Loading /etc/emacs/site-start.d/50autoconf.el (source)...done
Loading /etc/emacs/site-start.d/50devhelp.el (source)...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...done
Loading debian-ispell...done
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...done
Loading /etc/emacs/site-start.d/50global.el (source)...done
Loading /etc/emacs/site-start.d/50psvn.el (source)...done
Loading /etc/emacs/site-start.d/50python-docutils.el (source)...done
Loading /etc/emacs/site-start.d/50w3m-el.el (source)...done
For information about the GNU Project and its goals, type C-h C-p.
command-line-1: Unknown option `--parent-id'

3. nothing more happens until ctrl-c:

lz@ws1:~/Desktop/pida$ pida

Traceback (most recent call last):
  File "/usr/bin/pida", line 29, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/pida/core/application.py", line 141, in main
    exit_val = run_func(env)
  File "/usr/lib/python2.5/site-packages/pida/core/application.py", line 100, in run_pida
    b.loop_ui()
  File "/usr/lib/python2.5/site-packages/pida/core/boss.py", line 64, in loop_ui
    gtk.main()
KeyboardInterrupt
lz@ws1:~/Desktop/pida$ 

Any idea?

---

### Post by lbthrice on 2009-03-08
Workaround: this seems to be an issue with the emacs communication; the progran will launch if you choose vim as the embedded editor. i did this by rerunning the "first run wizard"

```
cd ~/.pida2
rm first_run_wizard
pida
```

then you will get the startup dialog...this time choose vim.

please note that the terminal output still gives

```
** (pida:3312): WARNING **: expected enumeration type MooPanePosition, but got GtkPositionType instead

```
someone who is more smarter than me might be able to explain what that means

----
REGARDING the behavior when emacs is chosen:

i don't think pida really loves emacs.
on my 8.10 install of pida 
Installed: 0.5.1-5
  Candidate: 0.5.1-5
  Version table:
 *** 0.5.1-5 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status

...if emacs is chosen as the embedded editor then pida does not open
only the pida loves you greeting is displayed...and it can only be made to go away with a force quit
also, an xemacs window pops open
here is the terminal output

```
** (pida:2790): WARNING **: expected enumeration type MooPanePosition, but got GtkPositionType instead
^CTraceback (most recent call last):
  File "/usr/bin/pida", line 29, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/pida/core/application.py", line 141, in main
    exit_val = run_func(env)
  File "/usr/lib/python2.5/site-packages/pida/core/application.py", line 94, in run_pida
    start_success = b.start()
  File "/usr/lib/python2.5/site-packages/pida/core/boss.py", line 49, in start
    self._sm.activate_editor(editor_name)
  File "/usr/lib/python2.5/site-packages/pida/core/servicemanager.py", line 239, in activate_editor
    self.editor.pre_start()
  File "/usr/lib/python2.5/site-packages/pida/editors/emacs/emacs.py", line 183, in pre_start
    if self._cb.connect():
  File "/usr/lib/python2.5/site-packages/pida/editors/emacs/emacs.py", line 81, in connect
    return self._server.connect()
  File "/usr/lib/python2.5/site-packages/pida/utils/emacs/emacscom.py", line 149, in connect
    self._socket = self._wait_connection()
  File "/usr/lib/python2.5/site-packages/pida/utils/emacs/emacscom.py", line 163, in _wait_connection
    conn, addr = s.accept()
  File "/usr/lib/python2.5/socket.py", line 172, in accept
    sock, addr = self._sock.accept()
KeyboardInterrupt

```

I am running intrepid using the gnome environment

---

### Post by mad-kow on 2009-12-15
I got Pida working with emacs.
Therefore i had to install the package emacs23. I had another version of emacs installed and in used, but Pida didn't start up with that one.

```
sudo apt-get install emacs23
```

After installing it i had to update the emacs alternatives.

```
cd /etc/alternatives
sudo mv emacs emacs.old
sudo ln -s /usr/bin/emacs23 emacs
```

That did the trick to me. If Pida starts up with Vim instead, execute:

```
rm ~/.pida2/first_run_wizard
```

This opens a window to choose the editor to be used on the next Pida startup.

More information on emacs support can be found here:
[http://pida.co.uk/wiki/EmacsSupport](http://pida.co.uk/wiki/EmacsSupport)

---

