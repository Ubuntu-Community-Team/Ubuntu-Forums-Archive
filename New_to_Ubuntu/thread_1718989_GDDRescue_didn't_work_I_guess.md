---
title: "GDDRescue didn't work I guess"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Zintha on 2011-04-01
Not sure which area of the forums to put this is... or if it even belongs here, but you guys have been amazingly supportive and have always pointing me in the right direction so if it doesn't belong here, let me know!

I work in an Office.
5 Computers.
 - 2 working with the software we need
 - 3 working with bugs, bugs that make it... unusable near sharp objects.

The software is unique, written over a few years around 1998-2003ish.
Works with XP and requires Word 2003 among some other programs.

2 Computers work great, trouble is, they're old and slow.
DDR Ram, 40gb hard drive (IDE no less) and PCI (not PCI-e) card.

So I built 3 nice shiny new ones. Nothing special, standard office computers. 
Installed XP, 2003 Word, the other programs it needs etc. Trouble is, when I load the software I need, get into a section of it, it gives me 

```

"************** Exception Text **************
System.ArgumentException: '1/1/0001 12:00:00 AM' is not a valid value for 'Value'. 'Value' should be between 'MinDate' and 'MaxDate'.
   at System.Windows.Forms.DateTimePicker.set_Value(DateTime value)
   at Swift2.main_Matter.loaddata() in C:\Documents and Settings\Nick\My Documents\Visual Studio Projects\WindowsApplication5\main_Matter.vb:line 1536
   at Swift2.main_Matter.main_Matter_Load(Object sender, EventArgs e) in C:\Documents and Settings\Nick\My Documents\Visual Studio Projects\WindowsApplication5\main_Matter.vb:line 1337
   at System.Windows.Forms.Form.OnLoad(EventArgs e)
   at System.Windows.Forms.Form.OnCreateControl()
   at System.Windows.Forms.Control.CreateControl(Boolean fIgnoreVisible)
   at System.Windows.Forms.Control.CreateControl()
   at System.Windows.Forms.Control.WmShowWindow(Message& m)
   at System.Windows.Forms.Control.WndProc(Message& m)
   at System.Windows.Forms.ScrollableControl.WndProc(Message& m)
   at System.Windows.Forms.ContainerControl.WndProc(Message& m)
   at System.Windows.Forms.Form.WmShowWindow(Message& m)
   at System.Windows.Forms.Form.WndProc(Message& m)
   at System.Windows.Forms.ControlNativeWindow.OnMessage(Message& m)
   at System.Windows.Forms.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)
"
```

Firstly, I don't know how to solve it, secondly.. We have working ones so why not copy them?

So I dive headfirst into the realm of cloning hard drives, past week or so been dealing with the issues of it.

Came across GDDRescue... or something like that, which copies them super easy. Seems to work too, however... when I put a new copied harddrive into a new computer. It refuses to boot.

Stalling on AGP440.sys, anything I can get to help just suggests "Oh go into safe mode and... etc". Which is super useful if I could get into safe mode.

So... I was wondering on any help or advice you guys could give, a direction you might be able to point me at or maybe even software that could do what I need (although I doubt that one, I understand old harddrive -> new motherboard = doesn't like it)

If you're at this stage, thanks for reading the whole thing. Its much appreciated.

- Oliver

---

