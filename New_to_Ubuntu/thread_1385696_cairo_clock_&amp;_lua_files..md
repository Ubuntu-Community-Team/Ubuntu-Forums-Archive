---
title: "cairo clock &amp; lua files."
date: 2010-01-19
forum: New to Ubuntu
---

### Post by ja660k on 2010-01-19
hey guys,

i have this lua file that is a cool clock looking thing.
and i dont know how to run it?

when i run
```
lua clock_rings-v1.1.1.lua
```
returns this:
```

lua: clock_rings-v1.1.1.lua:221: module 'cairo' not found:
	no field package.preload['cairo']
	no file './cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo/init.lua'
	no file '/usr/local/lib/lua/5.1/cairo.lua'
	no file '/usr/local/lib/lua/5.1/cairo/init.lua'
	no file '/usr/share/lua/5.1/cairo.lua'
	no file '/usr/share/lua/5.1/cairo/init.lua'
	no file './cairo.so'
	no file '/usr/local/lib/lua/5.1/cairo.so'
	no file '/usr/lib/lua/5.1/cairo.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
stack traceback:
	[C]: in function 'require'
	clock_rings-v1.1.1.lua:221: in main chunk
	[C]: ?


```

i dont know what to do?
thanks in advance

---

### Post by dmillerct on 2010-01-19
> **ja660k said:**
> hey guys,

i have this lua file that is a cool clock looking thing.
and i dont know how to run it?

when i run
```
lua clock_rings-v1.1.1.lua
```
returns this:
```

lua: clock_rings-v1.1.1.lua:221: module 'cairo' not found:
	no field package.preload['cairo']
	no file './cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo/init.lua'
	no file '/usr/local/lib/lua/5.1/cairo.lua'
	no file '/usr/local/lib/lua/5.1/cairo/init.lua'
	no file '/usr/share/lua/5.1/cairo.lua'
	no file '/usr/share/lua/5.1/cairo/init.lua'
	no file './cairo.so'
	no file '/usr/local/lib/lua/5.1/cairo.so'
	no file '/usr/lib/lua/5.1/cairo.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
stack traceback:
	[C]: in function 'require'
	clock_rings-v1.1.1.lua:221: in main chunk
	[C]: ?


```

i dont know what to do?
thanks in advance

You are probably trying to draw this on your desktop with conky.  

1. Make sure conky is installed sudo apt-get install conky You will need version 1.7.2 this is in the Karmic repos if you are on an older version you will need to download the deb from getdeb.

2. In your conkyrc file specify the following above TEXT:

lua_load /path/to/lua/file

3. Run conky and you should see the clock.

---

### Post by ja660k on 2010-01-20
that unfortunately didnt work :-(

```

conky -v
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)
...
...
Lua bindings:
 * Cairo
 * Imlib2

```

when i run conky in the terminal
```

Conky: llua_do_call: function conky_clock_rings execution failed: attempt to call a nil value

```

---

