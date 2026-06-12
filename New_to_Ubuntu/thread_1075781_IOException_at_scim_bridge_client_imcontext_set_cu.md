---
title: "IOException at scim_bridge_client_imcontext_set_cursor_location ()"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by flylehe on 2009-02-20
Hi,
I constantly get the same error message while using Emacs:
"An IOException occurred at cim_bridge_client_imcontext_set_cursor_location ()".
Thanks for your help!

Edit: 
The error should be "An IOException occurred at [COLOR="Red"]s[/COLOR]cim_bridge_client_imcontext_set_cursor_location ()".

---

### Post by LowSky on 2009-02-20
what are you using emacs for?

Did you code something poorly?

I seaerch google and it  cant even find that error.... ever!

Have you tried purging emacs and reinstalling it.

---

### Post by flylehe on 2009-02-20
sorry, "cim" should be "scim"

---

### Post by LowSky on 2009-02-23
sudo apt-get install scim-bridge-agent 

if that dont work try searching for a simular package, i found this on another post somewhere so i'm only guessing its right

then try running emacs, that might fix it

---

