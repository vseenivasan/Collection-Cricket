# COLLECTION-UI3141-3201

This collection of repositories is used for building `UI3141-3201`.
<!-- TOC depthFrom:2 updateOnSave:true -->

- [Installing Sources](#installing-sources)
- [Prerequisites for running or building](#prerequisites-for-running-or-building)
- [Interpret python source](#interpret-python-source)
- [Build procedure](#build-procedure)
- [Application Installer creation](#application-installer-creation)
- [Application release procedure](#application-release-procedure)

<!-- /TOC -->

## Installing Sources

<strong>From a tar file</strong>

Unpack the tar file in a convenient directory, using <code>tar -xzf <em><strong>tarfile.tgz</strong></em> -C <em><strong>destdir</strong></em></code>.

Then change directory to the <code><em><strong>destdir</strong></em></code>.

<strong>From gitlab-x.mcci.com</strong>

Clone the release tag repository from MCCI's gitlab-x server using the command:

```shell
git clone --recursive git@gitlab-x.mcci.com:Seenivasan/collection-ui3141_3201.git --branch <tag_name> --single-branch
```
For an example - Cloning for the release tag 'v1.0.0', replace the <tag_name> with v1.0.0 

Then change directories to the top level of the cloned repository.

## Prerequisites for running or building

<strong>On Windows:</strong>

Development environment

* OS - Windows 10 64 bit
* Python - 3.7.6
* wxpython - 4.0.7.post2
* pyserial - 3.4
* pyusb - 1.0.2
* libusb - 1.0.22b9
* libusb1 - 1.8
* pyinstaller - 3.6 

Download [python3.7.6](https://www.python.org/downloads/release/python-376/) and install

```shell
pip install wxpython==4.0.7.post2
pip install pyserial
pip install pyusb
pip install libusb
pip install libusb1
pip install pyinstaller
```

<strong>On Linux and Mac:</strong>

Development environment

* Linux OS - Ubuntu 20.4 64 bit
* Python - 3.8.2
* Mac OS - High Sierra
* Python - 3.7.0
* wxpython - 4.0.7.post2
* pyserial - 3.4
* pyusb - 1.0.2
* libusb - 1.0.22b9
* libusb1 - 1.8
* pyinstaller - 3.6  

```shell
sudo apt-get install python3
sudo apt-get install pip3
sudo pip3 install wxpython==4.0.7.post2
sudo pip3 install pyserial
sudo pip3 install pyusb
sudo pip3 install libusb
sudo pip3 install libusb1
sudo pip3 install pyinstaller
```

Note:
* If the installation of wxpython is not success, perform `sudo apt-get install build-essential libgtk-3-dev`
* Some times the installation of wxpython takes longer time (>30 minutes).

## Interpret python source

This is to ensure that the source can be interpreted without any error

Move to the directory `destdir/ui-3141-3201/src/`

<strong>On Windows:</strong>

```shell
python main.py
```

This show up application UI window on screen

<strong>On Linux and Mac:</strong>

```shell
python3 main.py
```

This show up application UI window on screen



## Build procedure

<strong>On Windows and Linux:</strong>

Move to the directory `destdir/ui-3141-3201/src/`

```shell
pyinstaller --distpath ./exeout/ --workpath ./exeout/build/ -F -w -i=./icons/mcci_logo.ico main.py -n UI3141-3201
```

The exe 'UI3141-3201' show up in `destdir/ui-3141-3201/src/exeout/`.

<strong>On Mac:</strong>

Move to the directory `destdir/ui-3141-3201/src/`

```shell
pyinstaller --distpath ./exeout/ --workpath ./exeout/build/ -F -w -i=./icons/mcci_logo.icns main.py -n UI3141-3201
```

The exe 'UI3141-3201' show up in `destdir/ui-3141-3201/src/exeout/`.

## Application Installer creation

<strong>On Windows:</strong>

Download [Inno Setup Compiler](https://jrsoftware.org/isdl.php#stable) and install

Run the Inno Setup Script file 'UI3141-3201-Windows' which is in `destdir/InstallerScript/`.

The App Installer 'UI3141-3201-Installer' show up in `destdir/AppInstaller/`.



<strong>On Linux:</strong>

There is no installer setup for Linux.



<strong>On Mac:</strong>

Download [Packages](http://s.sudre.free.fr/Software/Packages/about.html) and install

To know about [Packages](https://www.techrepublic.com/article/how-to-repackage-os-x-apps-with-packages/) more

Run the Package project file 'UI3141-3201-Mac' which is in `destdir/InstallerScript/`.

The App Installer 'UI3141-3201-Installer' show up in `destdir/AppInstaller/`.


## Application release procedure

<strong>On Windows:</strong>

Create a release directory with release version `MCCI-USB-Switch-3141-3201-GUI-Windows-<tag_name>`

Move the App Installer 'UI3141-3201-Installer' into the release directory and zip (compress) it, 
the name of zipped folder should be  `MCCI-USB-Switch-3141-3201-GUI-Windows-<tag_name>.zip`.

The Application Installer must be digitally signed before it can be deployed.

<strong>On Linux:</strong>

Create a release directory with release version `MCCI-USB-Switch-3141-3201-GUI-Linux-<tag_name>`.

Copy the exe 'UI3141-3201' from `destdir/exeout/` to release directory.

Copy the icons folder to the release directory.

Copy the doc folder to the release directory.

Run `tar -cvzf ./MCCI-USB-Switch-3141-3201-GUI-Linux-<tag>.tgz MCCI-USB-Switch-3141-3201-GUI-Linux-<tag_name>`

<strong>On Mac:</strong>

Create a release directory with release version `MCCI-USB-Switch-3141-3201-GUI-Mac-<tag_name>`.

Move the App Installer 'UI3141-3201-Installer' into the release directory and zip (compress) it, 
the name of zipped folder should be  `MCCI-USB-Switch-3141-3201-GUI-Mac-<tag_name>.zip`.

The Mac application and the Application Installer must be signed and notarized before it can be deployed.


