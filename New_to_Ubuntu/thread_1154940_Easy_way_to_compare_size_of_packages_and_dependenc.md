---
title: "Easy way to compare size of packages and dependencies?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by philliptweedie on 2009-05-10
Hey,

Just wandering if there was anyway to quickly check the total disk size required for a package including it's dependencies? I want the total to include dependencies already installed if that's possible.

Badly explained I know, but hopefully someone knows what I mean.

Cheers,

Phil

---

### Post by wizard10000 on 2009-05-10
> **philliptweedie said:**
> Hey,

Just wandering if there was anyway to quickly check the total disk size required for a package including it's dependencies? I want the total to include dependencies already installed if that's possible.

Badly explained I know, but hopefully someone knows what I mean.

Either apt-get or synaptic will give you that information.  If you try to install a package either will tell you how big the package with dependencies is before the final prompt to install.

---

### Post by unutbu on 2009-05-10
First, install the **apt-rdepends** package.
Then save this script in ~/bin/compute_total_pkg_size.py:

[PHP]
#!/usr/bin/env python
import sys
from subprocess import Popen,PIPE,STDOUT


__usage__='''
compute_total_pkg_size.py emacs
'''

pkg=sys.argv[1]


def report_lines(alist,max_len,vdiv,hline):
    '''
    alist is a list of tuples
    report_lines returns a list of strings
    '''
    result=[]
    svs=' '+vdiv+' '
    for row in alist:
        if row[0]=='-':
            line_string=hline
        else:
            data_justified=[str(elt).rjust(num) for elt,num in zip(row,max_len)]
            data_svs=svs.join(data_justified)
            line_list=[vdiv,data_svs,vdiv]
            line_string=' '.join(line_list)
        result.append(line_string)
    return result

def report_table(alist,corner='+',hdiv='-',vdiv='|',header=True):
    max_len=max_col_len(alist)
    hline_l=[corner,
             corner.join([hdiv.ljust(max_num+2,hdiv) 
                          for max_num in max_len]),
             corner]
    hline=''.join(hline_l)
    result=report_lines(alist,max_len,vdiv,hline)
    if header:
        new_result=[hline,result[0],hline,]
        new_result.extend(result[1:])
    else:
        new_result=[hline,]
        new_result.extend(result)
    new_result.append(hline)
    result='\n'.join(new_result)+'\n'
    return result

def max_col_len(alist):
    return [max([len(str(elt)) for elt in column]) for column in zip(*alist)]

def find_installed():
    '''
    Returns a list of all the packages installed on the computer
    '''
    proc=Popen("dpkg --get-selections | awk '/install/{print $1}'", 
               shell=True, stdout=PIPE, stderr=open('/dev/null'),)
    return proc.communicate()[0].split()

def get_size(pkg):
    '''
    Returns (download size, installed size) in KiB
    '''
    cmd='apt-cache show %s'%pkg
    proc=Popen(cmd, shell=True, stdout=PIPE, )
    size=0
    install_size=0
    for line in proc.communicate()[0].split('\n'):
        if line.startswith('Size: '):
            size=line.split()[-1]
        elif line.startswith('Installed-Size: '):
            install_size=line.split()[-1]
    return (int(size)/1024,int(install_size))

def get_dependencies(pkg):
    '''
    Returns all the (recursive) dependencies of a package
    '''
    cmd='apt-rdepends -s=DEPENDS %s'%pkg
    proc=Popen(cmd, shell=True, stdout=PIPE, )
    return proc.communicate()[0].strip().split('\n')
    
deps=get_dependencies(pkg)
installed_packages=find_installed()
needed_packages=list(set(deps)-set(installed_packages))
(sizes_dep,sizes_dep_installed)=zip(*[get_size(pkg) for pkg in deps])
(sizes_needed,sizes_needed_installed)=zip(*[get_size(pkg) for pkg in needed_packages])
data=[('Package (*=needed)','Download size (KiB)','Installed size (KiB)')]
for apkg,size,install_size in zip(deps,sizes_dep,sizes_dep_installed):
    if apkg in needed_packages:
        data.append(('%s *'%apkg,size,install_size))
    else:
        data.append((apkg,size,install_size))
print(report_table(data))

data=[('','Sizes (KiB)')]
data.append(('Total download size',sum(sizes_dep)))
data.append(('Total installed size',sum(sizes_dep_installed)))
data.append(('Total download size needed',sum(sizes_needed)))
data.append(('Total installed size needed',sum(sizes_needed_installed)))
print(report_table(data))

[/PHP]

Make it executable:
```

chmod 755 ~/bin/compute_total_pkg_size.py
```

Run it like this:```


compute_total_pkg_size.py emacs

```
(substitute whatever package you wish to analyze in place of 'emacs'.)

The output looks like this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
+------------------------+---------------------+----------------------+
|     Package (*=needed) | Download size (KiB) | Installed size (KiB) |
+------------------------+---------------------+----------------------+
|                emacs * |                   6 |                   36 |
|              emacs22 * |                1941 |                 5524 |
|   emacs22-bin-common * |                 163 |                  532 |
|       emacs22-common * |               18345 |                57896 |
|                   dpkg |                2177 |                 6872 |
|              coreutils |                1958 |                11084 |
|                libacl1 |                  17 |                   76 |
|               libattr1 |                  10 |                   68 |
|                  libc6 |                4262 |                10552 |
|              findutils |                 376 |                 1528 |
|                libgcc1 |                  25 |                   92 |
|           gcc-4.3-base |                 102 |                  164 |
|            libselinux1 |                  71 |                  180 |
|                   lzma |                  56 |                  168 |
|             libstdc++6 |                 325 |                 1172 |
|         emacsen-common |                  17 |                  144 |
|           bsdmainutils |                 169 |                  616 |
|               bsdutils |                  62 |                  184 |
|                    cpp |                  34 |                  104 |
|                cpp-4.3 |                3032 |                 7496 |
|              libgmp3c2 |                 233 |                  508 |
|           libmpfr1ldbl |                 340 |                  536 |
|            debianutils |                  55 |                  292 |
|            libncurses5 |                 177 |                  416 |
|           liblockfile1 |                  15 |                   92 |
|             libasound2 |                 347 |                 1228 |
|                libgif4 |                  37 |                  104 |
|                libice6 |                  46 |                  144 |
|             x11-common |                 353 |                  748 |
|                debconf |                 151 |                  964 |
|      debconf-english * |                   0 |                   20 |
|           debconf-i18n |                 143 |                 1024 |
| liblocale-gettext-perl |                  20 |                  108 |
|              perl-base |                 854 |                 2336 |
|       perlapi-5.10.0 * |                   0 |                    0 |
| libtext-charwidth-perl |                  11 |                   92 |
|     libtext-iconv-perl |                  16 |                  104 |
|  libtext-wrapi18n-perl |                   8 |                   68 |
|          debconf-2.0 * |                   0 |                    0 |
|               lsb-base |                  22 |                   84 |
|               libpam0g |                 108 |                  244 |
|         libpam-runtime |                  86 |                 1016 |
|            ncurses-bin |                 132 |                  292 |
|                    sed |                 197 |                  932 |
|              libjpeg62 |                  84 |                  196 |
|             libpng12-0 |                 162 |                  324 |
|                 zlib1g |                  73 |                  168 |
|                 libsm6 |                  22 |                   88 |
|               libtiff4 |                 122 |                  420 |
|               libx11-6 |                 606 |                 1168 |
|            libx11-data |                 165 |                 2116 |
|           libxcb-xlib0 |                   4 |                   68 |
|                libxcb1 |                  41 |                  160 |
|                libxau6 |                  11 |                   64 |
|              libxdmcp6 |                  16 |                   76 |
|                libxmu6 |                  50 |                  144 |
|               libxext6 |                  32 |                  124 |
|                 libxt6 |                 163 |                  380 |
|                libxpm4 |                  40 |                  124 |
|               xaw3dg * |                 152 |                  472 |
|          emacs22-gtk * |                1933 |                 5520 |
|           libglib2.0-0 |                 752 |                 1768 |
|               libpcre3 |                 207 |                  428 |
|            libgtk2.0-0 |                2210 |                 5576 |
|            libatk1.0-0 |                  49 |                  180 |
|              libcairo2 |                 426 |                  748 |
|         libfontconfig1 |                  90 |                  256 |
|      fontconfig-config |                  65 |                  332 |
|            gsfonts-x11 |                  10 |                  116 |
|                gsfonts |                3243 |                 4792 |
|                 defoma |                  98 |                  564 |
|               dialog * |                 257 |                 1364 |
|           libncursesw5 |                 198 |                  456 |
|                   file |                  41 |                  140 |
|              libmagic1 |                 350 |                 2364 |
|                   perl |                4433 |                13624 |
|               libdb4.6 |                 552 |                 1260 |
|               libgdbm3 |                  21 |                   80 |
|           perl-modules |                3195 |                16536 |
|               whiptail |                  34 |                   96 |
|            libnewt0.52 |                  57 |                  824 |
|              libslang2 |                 450 |                 1120 |
|               libpopt0 |                  28 |                  460 |
|           xfonts-utils |                  89 |                  484 |
|            libfontenc1 |                  17 |                   80 |
|           libfreetype6 |                 360 |                  676 |
|              libxfont1 |                 144 |                  316 |
|       xfonts-encodings |                 569 |                  836 |
|             xutils-dev |                 295 |                 1668 |
|     ttf-bitstream-vera |                 345 |                  732 |
|             ttf-dejavu |                   3 |                   68 |
|        ttf-dejavu-core |                1328 |                 2488 |
|       ttf-dejavu-extra |                2851 |                 5504 |
|           ttf-freefont |                1792 |                 3484 |
|                    ucf |                  60 |                  256 |
|             cdebconf * |                 153 |                  488 |
| libdebian-installer4 * |                  26 |                   92 |
|          libpango1.0-0 |                 285 |                  840 |
|             libdatrie0 |                  18 |                   92 |
|     libpango1.0-common |                  64 |                  208 |
|             fontconfig |                 133 |                  304 |
|               libthai0 |                  31 |                  100 |
|           libthai-data |                 158 |                  340 |
|                libxft2 |                  48 |                  136 |
|            libxrender1 |                  26 |                   92 |
|         libtextwrap1 * |                   9 |                   68 |
|              libexpat1 |                 129 |                  368 |
|          libpixman-1-0 |                 108 |                  316 |
|    libxcb-render-util0 |                   9 |                   72 |
|         libxcb-render0 |                   9 |                   88 |
|             libcomerr2 |                  41 |                   96 |
|               libcups2 |                 164 |                  368 |
|            libgnutls26 |                 359 |                 1044 |
|            libgcrypt11 |                 226 |                  496 |
|          libgpg-error0 |                  16 |                  200 |
|             libtasn1-3 |                  48 |                  160 |
|               libkrb53 |                 461 |                 1172 |
|           libkeyutils1 |                   5 |                   60 |
|       libgtk2.0-common |                 287 |                18516 |
|         libxcomposite1 |                  10 |                   64 |
|             libxfixes3 |                   9 |                   64 |
|            libxcursor1 |                  23 |                   84 |
|            libxdamage1 |                   9 |                   60 |
|                 libxi6 |                  26 |                   92 |
|           libxinerama1 |                   9 |                   60 |
|             libxrandr2 |                  21 |                   88 |
|          emacs22-nox * |                1684 |                 5064 |
+------------------------+---------------------+----------------------+

+-----------------------------+-------------+
|                             | Sizes (KiB) |
+-----------------------------+-------------+
|         Total download size |       69398 |
|        Total installed size |      228420 |
|  Total download size needed |       24669 |
| Total installed size needed |       77076 |
+-----------------------------+-------------+

```

---

### Post by philliptweedie on 2009-05-10
Thanks guys.

Cheers unutbu, script worked like a charm.

---

