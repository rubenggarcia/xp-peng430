# xp-peng430
How to use Xp-pen g430 grapich tablet in ubuntu 15.04 64bits

1) Install Wizardpen driver

Install wizardpen driver from:
https://launchpad.net/~doctormo/+archive/ubuntu/xorg-wizardpen/+build/4254509

Using this file:
xserver-xorg-input-wizardpen_0.8.2-0ubuntu2_amd64.deb (18.0 KiB)

2) Create Xorg config files

##### Create /usr/share/X11/xorg.conf.d/52-tablet.conf and fill with this:
    Section "InputClass"
    Identifier "UC-Logic tablet"
    MatchIsTablet "on"
    MatchProduct "UGTABLET TABLET G3 4x3"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    # Apply custom Options below.
    EndSection

##### Create /usr/share/X11/xorg.conf.d/70-wizardpen.conf and put this:


        Section "InputClass"
        Identifier "wizardpen"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        MatchTag "wizardpen"
        Driver "wizardpen"
        Option       "TopX"      "1506"
        Option       "TopY"      "2705"
        Option       "BottomX"   "31225"
        Option       "BottomY"   "30892"
        EndSection

3) Create (if not exists) /etc/X11/xorg.conf

wizardpen uses minor ABI version, you must override ABI requirements.

Add this lines to the xorg.conf file:

    Section "Server Flags"
    Option               "IgnoreABI"
    EndSection

Restart computer (or only lightdm) and enjou
