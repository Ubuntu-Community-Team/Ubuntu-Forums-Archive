---
title: "Fonts.Conf Error"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-08
Pretty simple problem:

I found that the fonts in Chromium looked dull, so, I found that if I added a file called: ".fonts.conf" in my home folder I could change the type of font.

Here is my .fonts.conf file:

```

  <?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
  <!-- ~/.fonts.conf for per-user font configuration -->
  <fontconfig>
    <alias>
      <family>serif</family>
      <prefer>
        <family>Droid Serif</family>
      </prefer>
    </alias>
    <alias>
      <family>sans-serif</family>
        <prefer>
          <family>Droid Sans</family>
        </prefer>
    </alias>
    <alias>
      <family>monospace</family>
      <prefer>
        <family>Droid Sans Mono</family>
       </prefer>
    </alias>
  </fontconfig>

```

Now, whenever I launch a terminal command (ANY command) I get the following error:

```

Fontconfig error: "~/.fonts.conf", line 1: XML or text declaration not at start of entity

```

---

### Post by abhiroopb on 2009-11-09
Bump!

---

### Post by abhiroopb on 2009-11-10
Bump (again!)

---

