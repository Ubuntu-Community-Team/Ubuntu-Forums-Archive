---
title: "glade-- generated code not compiling"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Macinbomzh on 2009-12-13
i ran glade-- to generate c++ sourcecode but when i compiled it with
```
g++ veim.cc -o veim `pkg-config gtkmm-2.4 --cflags --libs`

```it returned:```

/tmp/ccQcrbPN.o: In function `main_window::main_window()':
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x19): undefined reference to `VTT for main_window'
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x35): undefined reference to `VTT for main_window'
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x47): undefined reference to `main_window_glade::main_window_glade()'
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x4c): undefined reference to `vtable for main_window'
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x60): undefined reference to `vtable for main_window'
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x67): undefined reference to `vtable for main_window'
veim.cc:(.text._ZN11main_windowC1Ev[main_window::main_window()]+0x85): undefined reference to `VTT for main_window'
collect2: ld returned 1 exit status
```Can anyone help?

EDIT:
i found out the problem is with the gtkmm library, for some reason it is not recognized as valid
f.e.
```

#ifndef GTKMM_EXAMPLE_BUTTONS_H
#define GTKMM_EXAMPLE_BUTTONS_H

#include <gtkmm/window.h>
#include <gtkmm/button.h>

class Buttons : public Gtk::Window //this is not recognized
{
public:
  Buttons();
  virtual ~Buttons();

protected:
  //Signal handlers:
  void on_button_clicked();

  //Child widgets:
  Gtk::Button m_button;
};

#endif //GTKMM_EXAMPLE_BUTTONS_H


``````

#include <gtkmm/main.h>
#include "buttons.h"

int main(int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  Buttons buttons;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(buttons);

  return 0;
}


``````

#include "buttons.h"
#include <iostream>

Buttons::Buttons()
{
  m_button.add_pixlabel("info.xpm", "cool button");

  set_title("Pixmap'd buttons!");
  set_border_width(10);

  m_button.signal_clicked().connect( sigc::mem_fun(*this,
              &Buttons::on_button_clicked) );

  add(m_button);

  show_all_children();
}

Buttons::~Buttons()
{
}

void Buttons::on_button_clicked()
{
  std::cout << "The Button was clicked." << std::endl;
}


```it returns:```

/tmp/ccCJWgqM.o: In function `main':
main.cpp:(.text+0x38): undefined reference to `Buttons::Buttons()'
main.cpp:(.text+0x55): undefined reference to `Buttons::~Buttons()'
main.cpp:(.text+0x6e): undefined reference to `Buttons::~Buttons()'
collect2: ld returned 1 exit status

```anyone can think of a possible reason for that to happen?

---

