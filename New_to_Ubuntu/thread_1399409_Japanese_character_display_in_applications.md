---
title: "Japanese character display in applications?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by ybd on 2010-02-05
How would I go about displaying Japanese characters in, say, Rhythmbox? 

I tried downloading Japanese support packages from Synaptic, but maybe I got the wrong packages.

Just to clarify: I'm not using a Japanese-localized Ubuntu (and I don't want to.)

thanks for the help.

---

### Post by Bachstelze on 2010-02-05
Provided that your files use correct character encoding, all you would need is a font that provides the kanji/kana glyphs, for example:

```
sudo apt-get install ttf-sazanami-gothic
```

---

### Post by ybd on 2010-02-05
thanks... huh. I was certain I installed the package you mentioned before checking but I guess not. It works now.

---

