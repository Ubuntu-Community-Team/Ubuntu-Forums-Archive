---
title: "PanFlute not working"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by rebel01.nilesh on 2011-05-04
hello,

im on natty gnome classic desktop.
i installed panflute and it used to work fine. But suddenly after a restart it stopped working.
It sits there pretty on gnome panel but doesnt show any song information and remains idle.


HELP PLZ!!

---

### Post by rebel01.nilesh on 2011-05-05
i went to  ~/.local/share/panflute/applet.log and found this

Can neone point to me what the problem is and how to solve it?


WARNING [panflute.applet.player.Player] org.freedesktop.DBus.Python.mpd.CommandError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/panflute/daemon/mpris.py", line 446, in VolumeSet
    self.do_VolumeSet (volume)
  File "/usr/lib/pymodules/python2.7/panflute/daemon/mpd.py", line 264, in do_VolumeSet
    self.__active.setvol (volume)
  File "/usr/lib/pymodules/python2.7/mpd.py", line 167, in <lambda>
    return lambda *args: wrapper(command, args)
  File "/usr/lib/pymodules/python2.7/mpd.py", line 213, in _execute
    return retval()
  File "/usr/lib/pymodules/python2.7/mpd.py", line 312, in _fetch_nothing
    line = self._read_line()
  File "/usr/lib/pymodules/python2.7/mpd.py", line 233, in _read_line
    raise CommandError(error)
CommandError: [52@0] {setvol} problems setting volume

WARNING [panflute.applet.player.Player] org.freedesktop.DBus.Python.AssertionError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/panflute/daemon/mpris.py", line 460, in VolumeGet
    assert volume >= panflute.mpris.VOLUME_MIN and volume <= panflute.mpris.VOLUME_MAX
AssertionError

---

