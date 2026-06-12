---
title: "Compile error: gimpthumb-2.0 was not found in the pkg-config search path"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by rob86 on 2009-11-09
I'm trying to compile the latest version of emelfm2 with the optional plugin libgimpthumbnails.

The instructions aren't very easy to follow for me. I downloaded libgimpthumb  tarball from emelfm2 site, then I installed it with ./autogen and sudo checkinstall. The install went okay (no errors, not sure if I did it right though).

Then, it says to configure emelfm2 to compile the plugin, to type make WITH_THUMBS=1

When I type this, I get this error.
```
Package gimpthumb-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gimpthumb-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gimpthumb-2.0' found
Package gimpthumb-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gimpthumb-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gimpthumb-2.0' found
compiling 'plugins/optional/e2p_thumbs.c'
plugins/optional/e2p_thumbs.c:40:36: error: libgimpthumb/gimpthumb.h: No such file or directory
plugins/optional/e2p_thumbs.c: In function ‘_e2p_thumbs_make_store’:
plugins/optional/e2p_thumbs.c:124: error: ‘GIMP_TYPE_THUMBNAIL’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c:124: error: (Each undeclared identifier is reported only once
plugins/optional/e2p_thumbs.c:124: error: for each function it appears in.)
plugins/optional/e2p_thumbs.c: In function ‘_e2p_thumbs_clear_store’:
plugins/optional/e2p_thumbs.c:153: error: ‘GimpThumbnail’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c:153: error: ‘thm’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c: In function ‘_e2p_thumbs_replace_store’:
plugins/optional/e2p_thumbs.c:224: error: ‘GimpThumbnail’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c:224: error: ‘thumbnail’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c:297: warning: implicit declaration of function ‘gimp_thumbnail_new’
plugins/optional/e2p_thumbs.c:299: warning: implicit declaration of function ‘gimp_thumbnail_set_filename’
plugins/optional/e2p_thumbs.c:342: warning: implicit declaration of function ‘gimp_thumbnail_check_thumb’
plugins/optional/e2p_thumbs.c:342: error: ‘GIMP_THUMB_STATE_OK’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c:365: warning: implicit declaration of function ‘gimp_thumbnail_save_thumb’
plugins/optional/e2p_thumbs.c:386: warning: implicit declaration of function ‘gimp_thumbnail_peek_image’
plugins/optional/e2p_thumbs.c:386: error: ‘GIMP_THUMB_STATE_EXISTS’ undeclared (first use in this function)
plugins/optional/e2p_thumbs.c:402: warning: implicit declaration of function ‘gimp_thumbnail_load_thumb’
plugins/optional/e2p_thumbs.c:402: warning: assignment makes pointer from integer without a cast
plugins/optional/e2p_thumbs.c: In function ‘init_plugin’:
plugins/optional/e2p_thumbs.c:1812: warning: implicit declaration of function ‘gimp_thumb_init’
plugins/optional/e2p_thumbs.c:1831: error: ‘GIMP_THUMB_SIZE_NORMAL’ undeclared (first use in this function)
make: *** [objs/plugins/optional/e2p_thumbs.so] Error 1

```

Obviously it can't find gimpthumb, but I installed it, so I don't know what else to do to make it find it.What's the pkg-config search path? Can anyone help me? Thanks..

---

