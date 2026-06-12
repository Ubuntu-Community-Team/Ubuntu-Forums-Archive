---
title: "How to Execute a repeating Bash (Python?) Script"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by vertexoflife on 2009-04-20
Hello, 

I've just discovered a useful productivity script, and one that has been designed to work on Linux, asking the user if the current project is realyl worth their time. However, I am not sure how to execute it, or run it as it may be in order to take advantage of it. The script is below.

```
##!/usr/bin/env python

from time import sleep
import gtk

message_title = "Wasting Time?"
message_text = "Consider if this is really how I need to " .
               "be spending my time. Continue?"
minutes = 20
seconds = minutes * 60

class ProdBox(gtk.Dialog):
    def __init__(self):
        gtk.Dialog.__init__(self)

        self.ret = None

        self.connect("delete_event", self.delete_event)
        self.connect("destroy", self.quit)

        self.set_title(message_title)
        self.set_resizable(False)
        self.set_position(1)

        self.set_border_width(20)

        # Create box to pack widgets into
        self.message_label = gtk.Label(message_text)
        self.message_label.show()
        self.vbox.pack_start(self.message_label)

        self.hbox = gtk.HBox(False, 0)
        self.vbox.pack_start(self.hbox)

        # Create yes button
        self.yes_button = gtk.Button("_Yes")
        self.yes_button.set_border_width(10)
        self.yes_button.connect("clicked", self.yes)
        self.hbox.pack_start(self.yes_button, True, True, 0)
        self.yes_button.show()

        # Create no button
        self.no_button = gtk.Button("_No")
        self.no_button.set_border_width(10)
        self.no_button.connect("clicked", self.no)
        self.hbox.pack_start(self.no_button, True, True, 0)
        self.no_button.show()

        self.hbox.show()
        self.show()

    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def yes(self, widget):
        self.ret = "yes"
        self.quit()

    def no(self, widget):
        self.ret = "no"
        self.quit()

    def quit(self, *args):
        self.hide()
        self.destroy()
        gtk.main_quit()

def show_message():
    go = ProdBox()
    gtk.main()
    return go.ret

if __name__ == "__main__":
    while True:
        ret = show_message()
        if ret == "yes":
            sleep(seconds)
        else:
            break

```

---

### Post by steve101101 on 2009-04-20
you have to make it executable by right clicking the file and select properties. then you click permissions and select allow file execution as program.

---

### Post by vertexoflife on 2009-04-20
Thank you!

---

### Post by steve101101 on 2009-04-20
glad i could help.

---

### Post by steve101101 on 2009-04-20
also mark this as solved

---

