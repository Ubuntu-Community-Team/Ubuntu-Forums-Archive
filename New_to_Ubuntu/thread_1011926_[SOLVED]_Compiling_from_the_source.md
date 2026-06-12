---
title: "[SOLVED] Compiling from the source"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by shankhs on 2008-12-15
Hi!!!
I am trying to install glib-1.2.10 using the source code 
The ./configure is not giving me any error
But when I am doing a "make"
I am getting this:
```

gcc -DHAVE_CONFIG_H -I. -I. -I. -DG_LOG_DOMAIN=g_log_domain_glib -g -O2 -Wall -D_REENTRANT -c gstrfuncs.c  -fPIC -DPIC -o .libs/gstrfuncs.lo
gstrfuncs.c: In function 'g_printf_string_upper_bound':
gstrfuncs.c:870: error: expected ')' before string constant
gstrfuncs.c:1037: error: expected ')' before string constant
gstrfuncs.c:1080: error: expected ')' before string constant
gstrfuncs.c:1111: error: expected ')' before string constant
gstrfuncs.c: In function 'g_strdown':
gstrfuncs.c:1139: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strup':
gstrfuncs.c:1155: warning: pointer targets in assignment differ in signedness
gstrfuncs.c: In function 'g_strchug':
gstrfuncs.c:1314: warning: pointer targets in assignment differ in signedness
gstrfuncs.c:1317: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
make[2]: *** [gstrfuncs.lo] Error 1
make[2]: Leaving directory `/home/shankhs/glib-1.2.10'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/shankhs/glib-1.2.10'
make: *** [all-recursive-am] Error 2

```
There are lots of things before this I dont think they are of much importance( honestly, I dont know)
Please help me in installing Glib.
Thankyou

---

### Post by Bachstelze on 2008-12-15
Glib 1.2 is in the repos. Is there any reason why you want to install it from source?

---

### Post by trentscott4 on 2008-12-15
Why not apt-get the -dev package of libglib instead?

```
sudo apt-get install libglib1.2.10-dev
```

---

### Post by Bachstelze on 2008-12-15
> **trentscott4 said:**
> Why not apt-get the -dev package of libglib instead?

```
sudo apt-get install libglib1.2.10-dev
```

I'm pretty sure it's [FONT="Courier New"]libglib1.2-dev[/FONT].

---

### Post by Hospadar on 2008-12-15
Well first off,
Is there some compelling reason you can't just install it from the repositories (System->Administration->Synaptic) search for glib, install. If you're using a guide that says you need to build glib from source, it might be an old and or outdated guide.  Try just installing it from the repositories.

If indeed you do really need to compile it yourself, have you:
Installed the package "build-essential" (from synaptic)
Installed any dependancies needed to build glib (check their website, they probably have a guide to building their stuff with a list of dependancies)

Just from the errors you have, that'd be my guess about what the problem is.  In my own programming, I usually see errors like that when I'm forgetting some headers (files which tell the compiler which functions are in which library)

---

### Post by trentscott4 on 2008-12-15
> **HymnToLife said:**
> I'm pretty sure it's [FONT="Courier New"]libglib1.2-dev[/FONT].

Oops (typo), you're correct!

---

### Post by shankhs on 2008-12-15
Thankyou everybody.
I was learning how to build from the source files I got it I checked the dependencies installed it one by one.
Actually I was trying to run a network program that used glib.h and after googling I found that I need libglib1.2-dev to install, I got the source and was trying to build from it.
I installed libglib1.2-dev but I couldn't make my program which includes glib.h to compile successfully.
Do you have any idea why this is happening so. do i need to restart(after installation)???
OR is there any other way to include glib.h???

---

### Post by mc4man on 2008-12-15
You may want to post a link to the source your trying to compile.

Hardy doesn't use libglib1.2 (libglib2.0) and while you can install libglib1.2-dev you may need to make some changes in your configure. (or find an updated or similar package/source

---

### Post by shankhs on 2008-12-15
SNL is a small third party library that I want to install(its not in the repos)
I have attached the source code.
```

/*
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Library General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA
 */
 
/**** SAMPLE DESCRIPTION ****
 *
 * How this sample work:
 * 1. Create and run TCP client
 * 2. Connect with server
 * 3. Send message
 * 3. Receive message
 * 4. Disconnect and exit
 *
 * This sample shows how to create TCP client and run it using asynchronous
 * interface.
 */

#include <glib.h>
#include <snl.h>
#include <stdio.h>

/*******************************************************************************
    SIGNALS
 ******************************************************************************/
void    connect_signal  (SnlClient  *client,
                         SnlAddress *address,
                         gpointer   user_data)
{
    printf ("Client was connected\n");
    /* Enable auto receiving */
    snl_client_set_auto_receive (SNL_CLIENT (client), TRUE);
    /* Send message to server */
    snl_client_async_send (SNL_CLIENT (client), "Hi! I'm a async client!", 23, 5000000);
}

void    disconnect_signal  (SnlClient  *client,
                            gpointer   user_data)
{
    printf ("Clieant was disconnected\n");
}

void    send_signal     (SnlClient  *client,
                         gpointer   data,
                         gsize      data_len,
                         gpointer   user_data)
{
    printf ("Message: \'%s\' (%d bytes) was sent\n", (gchar *)data, data_len);
}

void    recv_signal     (SnlClient  *client,
                         gpointer   data,
                         gsize      data_len,
                         gpointer   user_data)
{
    printf ("Message: \'%s\' (%d bytes) was received\n", (gchar *)data, data_len); 
}

void    error_signal    (SnlClient  *client,
                         SnlError   *error,
                         gpointer   user_data)
{
    switch (error->error_operation) {
        case SNL_ERROR_OPERATION_CLIENT_CONNECT:
            printf ("Failed to connect, message: %s\n", error->generic_error->message);
            /* For some error SNL provides additional information, this example shows ho to use them properly */
            printf ("Failed to connect address: %s\n", snl_address_get_ip_address (SNL_ERROR_CLIENT_CONNECT (error)->address));
            break;
        case SNL_ERROR_OPERATION_CLIENT_DISCONNECT:
            printf ("Failed to disconnect, message: %s\n", error->generic_error->message);
            break;
        case SNL_ERROR_OPERATION_CLIENT_SEND:
            printf ("Failed to send, message: %s\n", error->generic_error->message);
            /* Another example showing how to use additional information about error */
            printf ("Failed to send this message: %s (%d bytes)\n", SNL_ERROR_CLIENT_SEND (error)->data, SNL_ERROR_CLIENT_SEND (error)->data_len);
            break;
        case SNL_ERROR_OPERATION_CLIENT_RECEIVE:
            printf ("Failed to receive, message: %s\n", error->generic_error->message);
            break;
        default:
            printf ("Unknown error, message: %s\n", error->generic_error->message);
    }
}

void    destroy_signal  (SnlClient  *client,
                         gpointer   user_data)
{
    printf ("Object is being destroyed....\n");
}

/*******************************************************************************
    PROGRAM - 'main' function
 ******************************************************************************/
int main    (void)  {
    SnlTcpClient    *client;
    SnlAddress      *address;
    GError          *error = NULL;
    gboolean        status;

    /* SNL will not work if GType and GThread weren't initialized! */
    g_type_init ();
    g_thread_init (NULL);
    
    /* Now you can initialize SNL */
    status = snl_main_init (&error);
    if (status == FALSE)    {
        printf ("Failed to initialize library, error message: %s\n", error->message);
        g_clear_error (&error);
        return 0;
    }
    
    /* Create new instance of SnlTcpClient type, prepare address and connect signals */
    client = snl_tcp_client_new (SNL_ADDRESS_FAMILY_IPV4);
    address = snl_address_new ("127.0.0.1", 2345);    
    g_signal_connect (SNL_CLIENT (client), "connect", G_CALLBACK (connect_signal), NULL);
    g_signal_connect (SNL_CLIENT (client), "disconnect", G_CALLBACK (disconnect_signal), NULL);
    g_signal_connect (SNL_CLIENT (client), "send", G_CALLBACK (send_signal), NULL);  
    g_signal_connect (SNL_CLIENT (client), "receive", G_CALLBACK (recv_signal), NULL);  
    g_signal_connect (SNL_CLIENT (client), "destroy", G_CALLBACK (destroy_signal), NULL); 
    g_signal_connect (SNL_CLIENT (client), "error", G_CALLBACK (error_signal), NULL); 
        
    /* Connect with server */
    snl_client_async_connect (SNL_CLIENT (client), address, 10000000);
    
    /* Now wait 20 secodns until async tasks complete */
    g_usleep (20000000);
    
    snl_object_destroy (SNL_OBJECT (client));
    snl_address_free (address);
    status = snl_main_finalize (&error);
    if (status == FALSE)    {
        printf ("Failed to finalize library, error message: %s\n", error->message);
        g_clear_error (&error);
    }
    
    return 0;
}

```
More info about SNL can be found at:
[http://www.gnomefiles.org/app.php?soft_id=2205](http://www.gnomefiles.org/app.php?soft_id=2205)

It says GTK+ and gobject(??) as an added dependencies I think I should install them also.
I searched the synaptic and got a bunch of stuffs which one I should install???

---

### Post by shankhs on 2008-12-15
For GTK+ I did 
sudo aptitude install gnome-core-devel build-essential
is it correct?
What about GObject?

---

### Post by mc4man on 2008-12-15
I've got to go to work, took a quick glance, this should build easily on Intrepid (8.10)
It requires libglib2.0  (2.18.0) (hardy uses 2.16

If your on intrepid install libglib2.0-dev

 > Package requirements (glib-2.0 >= 2.18.0)

Can't read your text att.
For GObject look at gobjc packages

---

### Post by shankhs on 2008-12-15
libglib2.0-dev is installed.
I am sorry if the att. did not open
```

/*
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Library General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA
 */
 
/**** SAMPLE DESCRIPTION ****
 *
 * How this sample work:
 * 1. Create and run TCP client
 * 2. Connect with server
 * 3. Send message
 * 3. Receive message
 * 4. Disconnect and exit
 *
 * This sample shows how to create TCP client and run it using asynchronous
 * interface.
 */

#include <glib.h>
#include <snl.h>
#include <stdio.h>

/*******************************************************************************
    SIGNALS
 ******************************************************************************/
void    connect_signal  (SnlClient  *client,
                         SnlAddress *address,
                         gpointer   user_data)
{
    printf ("Client was connected\n");
    /* Enable auto receiving */
    snl_client_set_auto_receive (SNL_CLIENT (client), TRUE);
    /* Send message to server */
    snl_client_async_send (SNL_CLIENT (client), "Hi! I'm a async client!", 23, 5000000);
}

void    disconnect_signal  (SnlClient  *client,
                            gpointer   user_data)
{
    printf ("Clieant was disconnected\n");
}

void    send_signal     (SnlClient  *client,
                         gpointer   data,
                         gsize      data_len,
                         gpointer   user_data)
{
    printf ("Message: \'%s\' (%d bytes) was sent\n", (gchar *)data, data_len);
}

void    recv_signal     (SnlClient  *client,
                         gpointer   data,
                         gsize      data_len,
                         gpointer   user_data)
{
    printf ("Message: \'%s\' (%d bytes) was received\n", (gchar *)data, data_len); 
}

void    error_signal    (SnlClient  *client,
                         SnlError   *error,
                         gpointer   user_data)
{
    switch (error->error_operation) {
        case SNL_ERROR_OPERATION_CLIENT_CONNECT:
            printf ("Failed to connect, message: %s\n", error->generic_error->message);
            /* For some error SNL provides additional information, this example shows ho to use them properly */
            printf ("Failed to connect address: %s\n", snl_address_get_ip_address (SNL_ERROR_CLIENT_CONNECT (error)->address));
            break;
        case SNL_ERROR_OPERATION_CLIENT_DISCONNECT:
            printf ("Failed to disconnect, message: %s\n", error->generic_error->message);
            break;
        case SNL_ERROR_OPERATION_CLIENT_SEND:
            printf ("Failed to send, message: %s\n", error->generic_error->message);
            /* Another example showing how to use additional information about error */
            printf ("Failed to send this message: %s (%d bytes)\n", SNL_ERROR_CLIENT_SEND (error)->data, SNL_ERROR_CLIENT_SEND (error)->data_len);
            break;
        case SNL_ERROR_OPERATION_CLIENT_RECEIVE:
            printf ("Failed to receive, message: %s\n", error->generic_error->message);
            break;
        default:
            printf ("Unknown error, message: %s\n", error->generic_error->message);
    }
}

void    destroy_signal  (SnlClient  *client,
                         gpointer   user_data)
{
    printf ("Object is being destroyed....\n");
}

/*******************************************************************************
    PROGRAM - 'main' function
 ******************************************************************************/
int main    (void)  {
    SnlTcpClient    *client;
    SnlAddress      *address;
    GError          *error = NULL;
    gboolean        status;

    /* SNL will not work if GType and GThread weren't initialized! */
    g_type_init ();
    g_thread_init (NULL);
    
    /* Now you can initialize SNL */
    status = snl_main_init (&error);
    if (status == FALSE)    {
        printf ("Failed to initialize library, error message: %s\n", error->message);
        g_clear_error (&error);
        return 0;
    }
    
    /* Create new instance of SnlTcpClient type, prepare address and connect signals */
    client = snl_tcp_client_new (SNL_ADDRESS_FAMILY_IPV4);
    address = snl_address_new ("127.0.0.1", 2345);    
    g_signal_connect (SNL_CLIENT (client), "connect", G_CALLBACK (connect_signal), NULL);
    g_signal_connect (SNL_CLIENT (client), "disconnect", G_CALLBACK (disconnect_signal), NULL);
    g_signal_connect (SNL_CLIENT (client), "send", G_CALLBACK (send_signal), NULL);  
    g_signal_connect (SNL_CLIENT (client), "receive", G_CALLBACK (recv_signal), NULL);  
    g_signal_connect (SNL_CLIENT (client), "destroy", G_CALLBACK (destroy_signal), NULL); 
    g_signal_connect (SNL_CLIENT (client), "error", G_CALLBACK (error_signal), NULL); 
        
    /* Connect with server */
    snl_client_async_connect (SNL_CLIENT (client), address, 10000000);
    
    /* Now wait 20 secodns until async tasks complete */
    g_usleep (20000000);
    
    snl_object_destroy (SNL_OBJECT (client));
    snl_address_free (address);
    status = snl_main_finalize (&error);
    if (status == FALSE)    {
        printf ("Failed to finalize library, error message: %s\n", error->message);
        g_clear_error (&error);
    }
    
    return 0;
}

```
I am trying to install SNL and when I am doing sudo checkinstall I am getting these errors:
```

----------------------------------------------------------------------
test -z "/usr/local/include/snl-1.0/snl" || /bin/mkdir -p "/usr/local/include/snl-1.0/snl"
/bin/mkdir: cannot create directory `/usr/local/include/snl-1.0': No such file or directory
make[3]: *** [install-libsnl_1_0_laHEADERS] Error 1
make[3]: Leaving directory `/home/shankhs/Desktop/shanx/hobby/small/small-network-library-1.0.0/snl'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/shankhs/Desktop/shanx/hobby/small/small-network-library-1.0.0/snl'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/shankhs/Desktop/shanx/hobby/small/small-network-library-1.0.0/snl'
make: *** [install-recursive] Error 1

```

I successfully installed SNL but still the code didnt compile because glib.h cant be include its in glib-2.0 now thats a big problem because glib.h has all the include files in glib-2.0/glib/ so glib.h has to be modified!!!!
what should I do?
Modify glib.h  or is there any other way?
Please help.

---

### Post by mc4man on 2008-12-15
> I successfully installed SNL but still the code didnt compile because glib.h cant be include its in glib-2.0 now thats a big problem because glib.h has all the include files in glib-2.0/glib/ so glib.h has to be modified!!!!

You lost me there.

Did a quick build on 8.10, went fine, didn't require anything but the libglib2.0-dev.

Made a checkinstall package to see what's installed, list is below.

If you want to try installing from package then cd to your source folder and from the prompt

```
sudo make uninstall
```

Then either delete the extracted folder and start over or again from the prompt
```
make clean
```
```
make distclean
```
Maybe you should configure to install to /usr

```
./configure --prefix=/usr
```

to get a successful checkinstall after the make, run

```
sudo checkinstall --fstrans=no
```

installed files (from the default ./configure

> /.
/usr
/usr/local
/usr/local/share
/usr/local/share/locale
/usr/local/share/locale/pl
/usr/local/share/locale/pl/LC_MESSAGES
/usr/local/share/locale/pl/LC_MESSAGES/snl-1.0.0.mo
/usr/local/share/gtk-doc
/usr/local/share/gtk-doc/html
/usr/local/share/gtk-doc/html/snl
/usr/local/share/gtk-doc/html/snl/index.html
/usr/local/share/gtk-doc/html/snl/snl-snl-peer.html
/usr/local/share/gtk-doc/html/snl/snl-snl-server.html
/usr/local/share/gtk-doc/html/snl/SnlUdpClient.html
/usr/local/share/gtk-doc/html/snl/SnlObject.html
/usr/local/share/gtk-doc/html/snl/ch01.html
/usr/local/share/gtk-doc/html/snl/snl.devhelp
/usr/local/share/gtk-doc/html/snl/right.png
/usr/local/share/gtk-doc/html/snl/SnlTcpServer.html
/usr/local/share/gtk-doc/html/snl/snl-snl-client.html
/usr/local/share/gtk-doc/html/snl/up.png
/usr/local/share/gtk-doc/html/snl/snl-snl-misc.html
/usr/local/share/gtk-doc/html/snl/SnlUdpPeer.html
/usr/local/share/gtk-doc/html/snl/snl.devhelp2
/usr/local/share/gtk-doc/html/snl/snl-snl-address.html
/usr/local/share/gtk-doc/html/snl/left.png
/usr/local/share/gtk-doc/html/snl/snl-snl-main.html
/usr/local/share/gtk-doc/html/snl/style.css
/usr/local/share/gtk-doc/html/snl/index.sgml
/usr/local/share/gtk-doc/html/snl/SnlTcpClient.html
/usr/local/share/gtk-doc/html/snl/snl-snl-error.html
/usr/local/share/gtk-doc/html/snl/home.png
/usr/local/lib
/usr/local/lib/pkgconfig
/usr/local/lib/pkgconfig/snl-1.0.pc
/usr/local/lib/libsnl-1.0.la
/usr/local/lib/libsnl-1.0.so.0.0.0
/usr/local/include
/usr/local/include/snl-1.0
/usr/local/include/snl-1.0/snl
/usr/local/include/snl-1.0/snl/snl-tcp-client.h
/usr/local/include/snl-1.0/snl/snl-client.h
/usr/local/include/snl-1.0/snl/snl.h
/usr/local/include/snl-1.0/snl/snl-main.h
/usr/local/include/snl-1.0/snl/snl-udp-peer.h
/usr/local/include/snl-1.0/snl/snl-misc.h
/usr/local/include/snl-1.0/snl/snl-address.h
/usr/local/include/snl-1.0/snl/snl-peer.h
/usr/local/include/snl-1.0/snl/snl-tcp-server.h
/usr/local/include/snl-1.0/snl/snl-error.h
/usr/local/include/snl-1.0/snl/snl-server.h
/usr/local/include/snl-1.0/snl/snl-udp-client.h
/usr/local/include/snl-1.0/snl/snl-object.h
/usr/share
/usr/share/doc
/usr/share/doc/small-network-library
/usr/share/doc/small-network-library/ChangeLog
/usr/share/doc/small-network-library/README
/usr/share/doc/small-network-library/INSTALL
/usr/share/doc/small-network-library/COPYING
/usr/share/doc/small-network-library/AUTHORS
/usr/share/doc/small-network-library/NEWS
/usr/local/lib/libsnl-1.0.so.0
/usr/local/lib/libsnl-1.0.so





---

### Post by shankhs on 2008-12-16
mc4man Thanx for replying..
If you look at the code there are 2 lines which says:
```

#include<glib.h>
#include<snl.h>

```
What I meant was : The basic of C programing tells me that if I am including something in linux it must be in /usr/include isn't it?
but this glib.h is in /usr/include/glib-2.0/ so I must do something like this:
```

#include <glib-2.0/glib.h>

```
But the main problem is in glib.h which says something like this
```

/* GLIB - Library of useful routines for C programming
 * Copyright (C) 1995-1997  Peter Mattis, Spencer Kimball and Josh MacDonald
 *
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the GNU Lesser General Public
 * License as published by the Free Software Foundation; either
 * version 2 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.	 See the GNU
 * Lesser General Public License for more details.
 *
 * You should have received a copy of the GNU Lesser General Public
 * License along with this library; if not, write to the
 * Free Software Foundation, Inc., 59 Temple Place - Suite 330,
 * Boston, MA 02111-1307, USA.
 */

/*
 * Modified by the GLib Team and others 1997-2000.  See the AUTHORS
 * file for a list of people on the GLib Team.  See the ChangeLog
 * files for a list of changes.  These files are distributed with
 * GLib at ftp://ftp.gtk.org/pub/gtk/. 
 */

#ifndef __G_TYPES_H__
#define __G_TYPES_H__

#include <glibconfig.h>

G_BEGIN_DECLS

/* Provide type definitions for commonly used types.
 *  These are useful because a "gint8" can be adjusted
 *  to be 1 byte (8 bits) on all platforms. Similarly and
 *  more importantly, "gint32" can be adjusted to be
 *  4 bytes (32 bits) on all platforms.
 */

typedef char   gchar;
typedef short  gshort;
typedef long   glong;
typedef int    gint;
typedef gint   gboolean;

typedef unsigned char   guchar;
typedef unsigned short  gushort;
typedef unsigned long   gulong;
typedef unsigned int    guint;

typedef float   gfloat;
typedef double  gdouble;

/* HAVE_LONG_DOUBLE doesn't work correctly on all platforms.
 * Since gldouble isn't used anywhere, just disable it for now */

#if 0
#ifdef HAVE_LONG_DOUBLE
typedef long double gldouble;
#else /* HAVE_LONG_DOUBLE */
typedef double gldouble;
#endif /* HAVE_LONG_DOUBLE */
#endif /* 0 */

typedef void* gpointer;
typedef const void *gconstpointer;

typedef gint            (*GCompareFunc)         (gconstpointer  a,
                                                 gconstpointer  b);
typedef gint            (*GCompareDataFunc)     (gconstpointer  a,
                                                 gconstpointer  b,
						 gpointer       user_data);
typedef gboolean        (*GEqualFunc)           (gconstpointer  a,
                                                 gconstpointer  b);
typedef void            (*GDestroyNotify)       (gpointer       data);
typedef void            (*GFunc)                (gpointer       data,
                                                 gpointer       user_data);
typedef guint           (*GHashFunc)            (gconstpointer  key);
typedef void            (*GHFunc)               (gpointer       key,
                                                 gpointer       value,
                                                 gpointer       user_data);
typedef void            (*GFreeFunc)            (gpointer       data);

/* Define some mathematical constants that aren't available
 * symbolically in some strict ISO C implementations.
 */
#define G_E     2.7182818284590452354E0
#define G_LN2   6.9314718055994530942E-1
#define G_LN10  2.3025850929940456840E0
#define G_PI    3.14159265358979323846E0
#define G_PI_2  1.57079632679489661923E0
#define G_PI_4  0.78539816339744830962E0
#define G_SQRT2 1.4142135623730950488E0

/* Portable endian checks and conversions
 *
 * glibconfig.h defines G_BYTE_ORDER which expands to one of
 * the below macros.
 */
#define G_LITTLE_ENDIAN 1234
#define G_BIG_ENDIAN    4321
#define G_PDP_ENDIAN    3412		/* unused, need specific PDP check */	


/* Basic bit swapping functions
 */
#define GUINT16_SWAP_LE_BE_CONSTANT(val)	((guint16) ( \
    (((guint16) (val) & (guint16) 0x00ffU) << 8) | \
    (((guint16) (val) & (guint16) 0xff00U) >> 8)))
#define GUINT32_SWAP_LE_BE_CONSTANT(val)	((guint32) ( \
    (((guint32) (val) & (guint32) 0x000000ffU) << 24) | \
    (((guint32) (val) & (guint32) 0x0000ff00U) <<  8) | \
    (((guint32) (val) & (guint32) 0x00ff0000U) >>  8) | \
    (((guint32) (val) & (guint32) 0xff000000U) >> 24)))

/* Intel specific stuff for speed
 */
#if defined (__i386__) && defined (__GNUC__) && __GNUC__ >= 2
#  define GUINT16_SWAP_LE_BE_X86(val) \
     (G_GNUC_EXTENSION					\
      ({ register guint16 __v;				\
	 if (__builtin_constant_p (val))		\
	   __v = GUINT16_SWAP_LE_BE_CONSTANT (val);	\
	 else						\
	   __asm__ __const__ ("rorw $8, %w0"		\
			      : "=r" (__v)		\
			      : "0" ((guint16) (val)));	\
	__v; }))
#  define GUINT16_SWAP_LE_BE(val) (GUINT16_SWAP_LE_BE_X86 (val))
#  if !defined(__i486__) && !defined(__i586__) \
      && !defined(__pentium__) && !defined(__i686__) && !defined(__pentiumpro__)
#     define GUINT32_SWAP_LE_BE_X86(val) \
        (G_GNUC_EXTENSION					\
         ({ register guint32 __v;				\
	    if (__builtin_constant_p (val))			\
	      __v = GUINT32_SWAP_LE_BE_CONSTANT (val);		\
	  else							\
	    __asm__ __const__ ("rorw $8, %w0\n\t"		\
			       "rorl $16, %0\n\t"		\
			       "rorw $8, %w0"			\
			       : "=r" (__v)			\
			       : "0" ((guint32) (val)));	\
	__v; }))
#  else /* 486 and higher has bswap */
#     define GUINT32_SWAP_LE_BE_X86(val) \
        (G_GNUC_EXTENSION					\
         ({ register guint32 __v;				\
	    if (__builtin_constant_p (val))			\
	      __v = GUINT32_SWAP_LE_BE_CONSTANT (val);		\
	  else							\
	    __asm__ __const__ ("bswap %0"			\
			       : "=r" (__v)			\
			       : "0" ((guint32) (val)));	\
	__v; }))
#  endif /* processor specific 32-bit stuff */
#  define GUINT32_SWAP_LE_BE(val) (GUINT32_SWAP_LE_BE_X86 (val))
#else /* !__i386__ */
#  define GUINT16_SWAP_LE_BE(val) (GUINT16_SWAP_LE_BE_CONSTANT (val))
#  define GUINT32_SWAP_LE_BE(val) (GUINT32_SWAP_LE_BE_CONSTANT (val))
#endif /* __i386__ */

#define GUINT64_SWAP_LE_BE_CONSTANT(val)	((guint64) ( \
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x00000000000000ffU)) << 56) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x000000000000ff00U)) << 40) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x0000000000ff0000U)) << 24) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x00000000ff000000U)) <<  8) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x000000ff00000000U)) >>  8) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x0000ff0000000000U)) >> 24) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0x00ff000000000000U)) >> 40) |	\
      (((guint64) (val) &						\
	(guint64) G_GINT64_CONSTANT(0xff00000000000000U)) >> 56)))
#if defined (__i386__) && defined (__GNUC__) && __GNUC__ >= 2
#  define GUINT64_SWAP_LE_BE_X86(val) \
	(__extension__						\
	 ({ union { guint64 __ll;				\
		    guint32 __l[2]; } __r;			\
	    if (__builtin_constant_p (val))			\
	      __r.__ll = GUINT64_SWAP_LE_BE_CONSTANT (val);	\
	    else						\
	      {							\
	 	union { guint64 __ll;				\
			guint32 __l[2]; } __w;			\
		__w.__ll = ((guint64) val);			\
		__r.__l[0] = GUINT32_SWAP_LE_BE (__w.__l[1]);	\
		__r.__l[1] = GUINT32_SWAP_LE_BE (__w.__l[0]);	\
	      }							\
	  __r.__ll; }))
#  define GUINT64_SWAP_LE_BE(val) (GUINT64_SWAP_LE_BE_X86 (val))
#else /* !__i386__ */
#  define GUINT64_SWAP_LE_BE(val) (GUINT64_SWAP_LE_BE_CONSTANT(val))
#endif

#define GUINT16_SWAP_LE_PDP(val)	((guint16) (val))
#define GUINT16_SWAP_BE_PDP(val)	(GUINT16_SWAP_LE_BE (val))
#define GUINT32_SWAP_LE_PDP(val)	((guint32) ( \
    (((guint32) (val) & (guint32) 0x0000ffffU) << 16) | \
    (((guint32) (val) & (guint32) 0xffff0000U) >> 16)))
#define GUINT32_SWAP_BE_PDP(val)	((guint32) ( \
    (((guint32) (val) & (guint32) 0x00ff00ffU) << 8) | \
    (((guint32) (val) & (guint32) 0xff00ff00U) >> 8)))

/* The G*_TO_?E() macros are defined in glibconfig.h.
 * The transformation is symmetric, so the FROM just maps to the TO.
 */
#define GINT16_FROM_LE(val)	(GINT16_TO_LE (val))
#define GUINT16_FROM_LE(val)	(GUINT16_TO_LE (val))
#define GINT16_FROM_BE(val)	(GINT16_TO_BE (val))
#define GUINT16_FROM_BE(val)	(GUINT16_TO_BE (val))
#define GINT32_FROM_LE(val)	(GINT32_TO_LE (val))
#define GUINT32_FROM_LE(val)	(GUINT32_TO_LE (val))
#define GINT32_FROM_BE(val)	(GINT32_TO_BE (val))
#define GUINT32_FROM_BE(val)	(GUINT32_TO_BE (val))

#define GINT64_FROM_LE(val)	(GINT64_TO_LE (val))
#define GUINT64_FROM_LE(val)	(GUINT64_TO_LE (val))
#define GINT64_FROM_BE(val)	(GINT64_TO_BE (val))
#define GUINT64_FROM_BE(val)	(GUINT64_TO_BE (val))

#define GLONG_FROM_LE(val)	(GLONG_TO_LE (val))
#define GULONG_FROM_LE(val)	(GULONG_TO_LE (val))
#define GLONG_FROM_BE(val)	(GLONG_TO_BE (val))
#define GULONG_FROM_BE(val)	(GULONG_TO_BE (val))

#define GINT_FROM_LE(val)	(GINT_TO_LE (val))
#define GUINT_FROM_LE(val)	(GUINT_TO_LE (val))
#define GINT_FROM_BE(val)	(GINT_TO_BE (val))
#define GUINT_FROM_BE(val)	(GUINT_TO_BE (val))


/* Portable versions of host-network order stuff
 */
#define g_ntohl(val) (GUINT32_FROM_BE (val))
#define g_ntohs(val) (GUINT16_FROM_BE (val))
#define g_htonl(val) (GUINT32_TO_BE (val))
#define g_htons(val) (GUINT16_TO_BE (val))

/* IEEE Standard 754 Single Precision Storage Format (gfloat):
 *
 *        31 30           23 22            0
 * +--------+---------------+---------------+
 * | s 1bit | e[30:23] 8bit | f[22:0] 23bit |
 * +--------+---------------+---------------+
 * B0------------------->B1------->B2-->B3-->
 *
 * IEEE Standard 754 Double Precision Storage Format (gdouble):
 *
 *        63 62            52 51            32   31            0
 * +--------+----------------+----------------+ +---------------+
 * | s 1bit | e[62:52] 11bit | f[51:32] 20bit | | f[31:0] 32bit |
 * +--------+----------------+----------------+ +---------------+
 * B0--------------->B1---------->B2--->B3---->  B4->B5->B6->B7->
 */
/* subtract from biased_exponent to form base2 exponent (normal numbers) */
typedef union  _GDoubleIEEE754	GDoubleIEEE754;
typedef union  _GFloatIEEE754	GFloatIEEE754;
#define G_IEEE754_FLOAT_BIAS	(127)
#define G_IEEE754_DOUBLE_BIAS	(1023)
/* multiply with base2 exponent to get base10 exponent (nomal numbers) */
#define G_LOG_2_BASE_10		(0.30102999566398119521)
#if G_BYTE_ORDER == G_LITTLE_ENDIAN
union _GFloatIEEE754
{
  gfloat v_float;
  struct {
    guint mantissa : 23;
    guint biased_exponent : 8;
    guint sign : 1;
  } mpn;
};
union _GDoubleIEEE754
{
  gdouble v_double;
  struct {
    guint mantissa_low : 32;
    guint mantissa_high : 20;
    guint biased_exponent : 11;
    guint sign : 1;
  } mpn;
};
#elif G_BYTE_ORDER == G_BIG_ENDIAN
union _GFloatIEEE754
{
  gfloat v_float;
  struct {
    guint sign : 1;
    guint biased_exponent : 8;
    guint mantissa : 23;
  } mpn;
};
union _GDoubleIEEE754
{
  gdouble v_double;
  struct {
    guint sign : 1;
    guint biased_exponent : 11;
    guint mantissa_high : 20;
    guint mantissa_low : 32;
  } mpn;
};
#else /* !G_LITTLE_ENDIAN && !G_BIG_ENDIAN */
#error unknown ENDIAN type
#endif /* !G_LITTLE_ENDIAN && !G_BIG_ENDIAN */

typedef struct _GTimeVal                GTimeVal;

struct _GTimeVal
{
  glong tv_sec;
  glong tv_usec;
};

G_END_DECLS

/* We prefix variable declarations so they can
 * properly get exported in windows dlls.
 */
#ifndef GLIB_VAR
#  ifdef G_PLATFORM_WIN32
#    ifdef GLIB_STATIC_COMPILATION
#      define GLIB_VAR extern
#    else /* !GLIB_STATIC_COMPILATION */
#      ifdef GLIB_COMPILATION
#        ifdef DLL_EXPORT
#          define GLIB_VAR __declspec(dllexport)
#        else /* !DLL_EXPORT */
#          define GLIB_VAR extern
#        endif /* !DLL_EXPORT */
#      else /* !GLIB_COMPILATION */
#        define GLIB_VAR extern __declspec(dllimport)
#      endif /* !GLIB_COMPILATION */
#    endif /* !GLIB_STATIC_COMPILATION */
#  else /* !G_PLATFORM_WIN32 */
#    define GLIB_VAR extern
#  endif /* !G_PLATFORM_WIN32 */
#endif /* GLIB_VAR */

#endif /* __G_TYPES_H__ */


```
Now I figured out that glibconfig.h is in /usr/lib/glib/include/glibconfig.h now how would a C program knows that address? It will unsuccessfully search for /usr/include/glibconfig.h and return an error.
Am I missing something?
Please help me.

---

### Post by mc4man on 2008-12-16
Unfortunately I can't test the app and honestly can't say (or know) if what your thinking is true.
I can say that looking thru the config. log, make file and the make output that there is no indication of any errors and that the proper header files wweren't found. From all indications the build seems to be correct.

You may be better served by posting in this forum

[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

For clarity's sake are you saying the configure, make and install went fine and that the issue is the app doesn't work?

snips

> GLIB_CFLAGS='-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  '
GLIB_GENMARSHAL='/usr/bin/glib-genmarshal'
GLIB_LIBS='-lglib-2.0  '
GLIB_MKENUMS='/usr/bin/glib-mkenums'
GMOFILES=' pl.gmo'
GMSGFMT='/usr/bin/msgfmt'
GOBJECT_CFLAGS='-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  '
GOBJECT_LIBS='-lgobject-2.0 -lglib-2.0  '
GREP='/bin/grep'
GTHREAD_CFLAGS='-pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  '

D> PACKAGE_DATA_DIR=\"/usr/share\" -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -g -O2 -MT libsnl_1_0_la-backend-linux.lo -MD  -f .deps/libsnl_1_0_la-backend-linux.Tpo .deps/libsnl_1_0_la-backend-linux.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc -Wall  -g -O2 -version-info 0:0:0  -o libsnl-1.0.la -rpath /usr/lib libsnl_1_0_la-builtin-types.lo libsnl_1_0_la-marshal.lo libsnl_1_0_la-internal.lo libsnl_1_0_la-snl-object.lo libsnl_1_0_la-snl-error.lo libsnl_1_0_la-snl-misc.lo libsnl_1_0_la-snl-address.lo libsnl_1_0_la-snl-server.lo libsnl_1_0_la-snl-client.lo libsnl_1_0_la-snl-main.lo libsnl_1_0_la-snl-tcp-server.lo libsnl_1_0_la-snl-tcp-client.lo libsnl_1_0_la-snl-peer.lo libsnl_1_0_la-snl-udp-peer.lo libsnl_1_0_la-snl-udp-client.lo libsnl_1_0_la-backend-linux.lo -lglib-2.0 -pthread -lgthread-2.0 -lrt -lglib-2.0 -lgobject-2.0 -lglib-2.0  


---

### Post by shankhs on 2008-12-16
yes exactly that the app doesnt work....:(
I dont know what is going wrong.
I posted it here:
[http://ubuntuforums.org/showthread.php?p=6377885#post6377885](http://ubuntuforums.org/showthread.php?p=6377885#post6377885)

I hope somebody helps...
It has been an adventurous night googling about some C basics and Linux programming but still couldnt compile but I am not getting this stop me I would fix this and post a nice HowTo for all the newbies like me so they no more fear compiling the source files and get into development without too much hassle.

---

### Post by mc4man on 2008-12-16
From your other post
> Now to test the installation I ran one of the sample programs here is the code

I was wondering what you were posting and or doing.

Made me curious so I decided to install and try running a 'sample'

The readme implies you need to run 2 programs at once so i set up 2 terminals at the sample prompt.
It seemed to work ok. (kept in mind I don't now much about this.

Ran the first terminal, then the second.

> doug@doug-desktop:~/Desktop/small-network-library-1.0.0/samples$ ./tcp_server_async
[COLOR="Red"]Server was started[/COLOR]
[COLOR="Blue"]Receive message...
Received data: 'Hi! I'm a async client!', lenght: 23 bytes
Send message...[/COLOR]


> 
doug@doug-desktop:~/Desktop/small-network-library-1.0.0/samples$  ./tcp_client_async
[COLOR="Red"]Client was connected
Message: 'Hi! I'm a async client!' (23 bytes) was sent[/COLOR]
[COLOR="Blue"]Message: 'Reply from server' (17 bytes) was received[/COLOR]

First terminal showed the red, started second terminal, then red in second terminal, followed by blue in first terminal, then blue in second

---

### Post by shankhs on 2008-12-16
Let me explain to you whats happening I did the same thing as you did and it worked exactly the same way as you have posted(Thankyou for your interest).
./tcp_server_sync
```

Starts server...
Accept connections server...
Receive message...
Received data: 'Sample message', lenght: 14 bytes
Send message...
Stop server...


```
./tcp_client_sync
```

Connect...
Send message...
Receive message...
Received data: 'Reply from server', lenght: 17 bytes
Exit...


```
But when I started developing in SNL I ran into compilation errors , then I tried to compile the tcp_server_sync.c in samples and I got these errors:
```

[COLOR="Red"]tcp_server_sync.c:29:18: error: glib.h: No such file or directory
tcp_server_sync.c:30:17: error: snl.h: No such file or directory[/COLOR]
tcp_server_sync.c: In function &#8216;main&#8217;:
tcp_server_sync.c:34: error: &#8216;SnlTcpServer&#8217; undeclared (first use in this function)
tcp_server_sync.c:34: error: (Each undeclared identifier is reported only once
tcp_server_sync.c:34: error: for each function it appears in.)
tcp_server_sync.c:34: error: &#8216;server&#8217; undeclared (first use in this function)
tcp_server_sync.c:35: error: &#8216;SnlTcpClient&#8217; undeclared (first use in this function)
tcp_server_sync.c:35: error: &#8216;client&#8217; undeclared (first use in this function)
tcp_server_sync.c:36: error: &#8216;SnlAddress&#8217; undeclared (first use in this function)
tcp_server_sync.c:36: error: &#8216;address&#8217; undeclared (first use in this function)
tcp_server_sync.c:37: error: &#8216;GError&#8217; undeclared (first use in this function)
tcp_server_sync.c:37: error: &#8216;error&#8217; undeclared (first use in this function)
tcp_server_sync.c:38: error: &#8216;gboolean&#8217; undeclared (first use in this function)
tcp_server_sync.c:38: error: expected &#8216;;&#8217; before &#8216;status&#8217;
tcp_server_sync.c:39: error: &#8216;gchar&#8217; undeclared (first use in this function)
tcp_server_sync.c:39: error: expected &#8216;;&#8217; before &#8216;buffer&#8217;
tcp_server_sync.c:40: error: &#8216;gint&#8217; undeclared (first use in this function)
tcp_server_sync.c:40: error: expected &#8216;;&#8217; before &#8216;data_len&#8217;
tcp_server_sync.c:47: error: &#8216;status&#8217; undeclared (first use in this function)
tcp_server_sync.c:48: error: &#8216;FALSE&#8217; undeclared (first use in this function)
tcp_server_sync.c:56: error: &#8216;SNL_ADDRESS_FAMILY_IPV4&#8217; undeclared (first use in this function)
tcp_server_sync.c:58: error: &#8216;TRUE&#8217; undeclared (first use in this function)
tcp_server_sync.c:76: error: &#8216;buffer&#8217; undeclared (first use in this function)
tcp_server_sync.c:76: error: &#8216;data_len&#8217; undeclared (first use in this function)

```
SO I am trying to figure out what went wrong!!!!

---

### Post by mc4man on 2008-12-16
There was a bug fix release yesterday, maybe you'll have better luck there

[http://code.google.com/p/snllibrary/downloads/detail?name=small-network-library-1.0.1.tar.bz2&can=2&q=](http://code.google.com/p/snllibrary/downloads/detail?name=small-network-library-1.0.1.tar.bz2&can=2&q=)

Where to post issues
[http://code.google.com/p/snllibrary/issues/list](http://code.google.com/p/snllibrary/issues/list)

---

### Post by shankhs on 2008-12-16
thanx mc4man for all the time you gave to me in solving my problem.
Thanx once again to give the link to post all the issues with SNL.
Thankyou very much.

---

