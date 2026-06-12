---
title: "expected specifier-qualifier-list"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by ostar2 on 2011-06-06
can someone fix these files there i have trying to compile Spalah flash form over a year now.

---

### Post by ostar2 on 2011-06-06
These are the errors I get:

In file included from spa-draw-area.h:28:0,
                 from main.c:22:
spa-svg.h:54:5: error: expected specifier-qualifier-list before ‘ArtBpath’
spa-svg.h:79:3: warning: data definition has no type or storage class
spa-svg.h:79:3: warning: type defaults to ‘int’ in declaration of ‘class’
spa-svg.h:80:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
spa-svg.h:81:34: warning: type defaults to ‘int’ in declaration of ‘ArtBpath’
spa-svg.h:81:48: error: expected ‘)’ before ‘*’ token


and this the code:

```

#ifndef  __SPA_SVG_H__
#define __SPA_SVG_H__

/*
 *    Spalah SVG Args parser 0.01
 *
 *
 * Authors:
 *   Anatoly Podlesnuk <beerubeer@ukr.net>
 *
 * Copyright (C) 2004 Anatoly Podlesnuk
 *
 * Released under GNU GPL, read the file 'COPYING' for more information
 */

#include <glib.h>

//#include <gtk/gtk.h>
#include <gnome.h>
//#include <libxml/parser.h>

#ifdef __cplusplus
extern "C"
{
#endif                /* __cplusplus */

  // #define DEFAULT_RESOLUTION (96.0)
  //#define CM_TO_PIXELS(cm) (cm/2.54*RESOLUTION)
  //#define MM_TO_PIXELS(mm) (mm/25.4*RESOLUTION)
  //#define PT_TO_PIXELS(pt) (pt/72*RESOLUTION)

  typedef struct _SpaSVGArgs SpaSVGArgs;

  struct _SpaSVGArgs
  {
    double width;
    double height;
    double x,
      y,
      x2,
      y2;
    double stroke_width;
    double affine[6];
    double font_size;
    gchar *font_family;
    gchar *name,
     *transform,
     *flash_transform,
     *flash_transform_name,
     *text;
    gchar *id;
    guint rgba_stroke,
      rgba_fill;
    ArtBpath *path;
    double a_begin,
      a_dur;
    double a_from,
      a_to;
    //GHashTable *args;
  };

  SpaSVGArgs *spa_svg_svgargs_new (SpaSVGArgs * svgparent);

#define DEFAULT_RESOLUTION 96.0

  enum
  {
    SPA_CM,
    SPA_MM,
    SPA_PT
  };

  void spa_svg_parse_transform (gchar * value, double *affine);
  double spa_svg_value_to_double (gchar * value);
  gboolean spa_svg_set_resolution (double resolution);
  double spa_svg_get_resolution (void);
  double spa_svg_value_to_pixels (gint units, double value);

  class;
     ArtBpath * sp_svg_read_path (const char *str);
  char *sp_svg_write_path (const ArtBpath, ... *bpath);

#ifdef __cplusplus
}
#endif                /* __cplusplus */
#endif                             /*__SPA_SVG_H__*/

```

---

