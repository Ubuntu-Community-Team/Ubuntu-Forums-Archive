---
title: "How do I assign a custom Keyboard Shortcut?"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by GoldenAxe on 2011-04-02
Should be incredibly easy, I know!

I want to use the inbuilt Keyboard Shortcuts (System>Preferences>Keyboard Shortcuts) to open files and folders.

I don't know how to write the Custom Shortcut command. For example, I've want to open document called To Do. So I've tried putting:

Open '/home/goldenaxe/Dropbox/Projects/To Do.doc

This produces an error message when the assigned key is pressed. 
So how do I write a coherent command to open a folder? The document location bit is correct.

A single example is all I need. I can figure it out from there.

Assistance really appreciated (I've trawled through the forums and all the questions I can find are about four million times more complex). I just want the most basic advice.

---

### Post by leviathan8 on 2011-04-02
You might want to consider installing ccsm. Go to Ubuntu Software Center and search for ccsm and choose to install Advanced Desktop Effects Settings. Once you are done, open it under Preferences -> CompizConfig Settings Manager. Head to General -> Commands and you will be free to assign your keyboard shortcuts from there. In the Commands tab you write the program name and/or file you want to open (in your case ooffice -writer "/home/goldenaxe/Dropbox/Projects/To Do.doc") and then you select the Key Bindings tab and assign a shortcut for it, according to your command line number. This is less preferred method for what you want to do, but it works like a charm if you wish to open only applications. I have set my key binding button as Super (or Windows key) so it doesn't interfere with other keyboard shortcuts.

---

### Post by GoldenAxe on 2011-04-02
Thanks for that. 

Actually, it turns out I just needed to alter the command line stuff in the Custom box. 

I didn't realise that the commands for the custom box as for the same as those for the Terminal.

The CCSM editor is a very useful tip though. Will use that too.

Thank you for responding.

---

