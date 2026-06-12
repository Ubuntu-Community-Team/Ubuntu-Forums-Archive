---
title: "Python easy_install numpy"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by flebber on 2011-07-19
I am using the default python 2.7 and have installed easy_install via package manager.

However after then using easy_install to build numpy when I attempt to install scipy, it states the numpy dependencies are missing, can i force a reinstall of numpy?

This is my log.
```
Setting up python-setuptools (0.6.15-1ubuntu1) ...
sayth@sayth-TravelMate-5740G:~/Downloads$ sudo easy_install numpy
Searching for numpy
Best match: numpy 1.5.1
numpy 1.5.1 is already the active version in easy-install.pth

Using /usr/lib/pymodules/python2.7
Processing dependencies for numpy
Finished processing dependencies for numpy
sayth@sayth-TravelMate-5740G:~/Downloads$ sudo easy_install scipy
Searching for scipy
Reading http://pypi.python.org/simple/scipy/
Reading http://www.scipy.org
Reading http://new.scipy.org/Wiki/Download
Reading http://sourceforge.net/project/showfiles.php?group_id=27747&package_id=19531
Best match: scipy 0.9.0
Downloading http://sourceforge.net/projects/scipy/files/scipy/0.9.0/scipy-0.9.0.tar.gz/download
Processing download
Running scipy-0.9.0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-lw90zo/scipy-0.9.0/egg-dist-tmp-FK9M0a
Warning: No configuration returned, assuming unavailable./usr/lib/pymodules/python2.7/numpy/distutils/system_info.py:1399: UserWarning: 
    Atlas (http://math-atlas.sourceforge.net/) libraries not found.
    Directories to search for the libraries can be specified in the
    numpy/distutils/site.cfg file (section [atlas]) or by setting
    the ATLAS environment variable.
  warnings.warn(AtlasNotFoundError.__doc__)
/usr/lib/pymodules/python2.7/numpy/distutils/system_info.py:1408: UserWarning: 
    Blas (http://www.netlib.org/blas/) libraries not found.
    Directories to search for the libraries can be specified in the
    numpy/distutils/site.cfg file (section [blas]) or by setting
    the BLAS environment variable.
  warnings.warn(BlasNotFoundError.__doc__)
/usr/lib/pymodules/python2.7/numpy/distutils/system_info.py:1411: UserWarning: 
    Blas (http://www.netlib.org/blas/) sources not found.
    Directories to search for the sources can be specified in the
    numpy/distutils/site.cfg file (section [blas_src]) or by setting
    the BLAS_SRC environment variable.
  warnings.warn(BlasSrcNotFoundError.__doc__)
error: 
    Blas (http://www.netlib.org/blas/) libraries not found.
    Directories to search for the libraries can be specified in the
    numpy/distutils/site.cfg file (section [blas]) or by setting
    the BLAS environment variable.
sayth@sayth-TravelMate-5740G:~/Downloads$ sudo apt-get install numpy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package numpy
sayth@sayth-TravelMate-5740G:~/Downloads$ 

```

---

### Post by raja.genupula on 2011-07-19
run update once and then again try to install

---

### Post by flebber on 2011-07-19
Ubunutu rebooted and I ran update but still same error.

---

### Post by raja.genupula on 2011-07-20
just give me the way how you are trying to install the application . give me the output of it 
. was your application have  links in source.list?

---

### Post by flebber on 2011-07-20
I have fully removed pip and setuptools and numpy. Done a full reinstall of python 2.7.

Now just reading up on virtualenv and once that is set up I will start again.

---

