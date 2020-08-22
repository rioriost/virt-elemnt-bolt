# virt-elemnt-bolt
overlay 'virtual' ELEMNT BOLT on movies

![Virtual ELEMNT BOLT](images/20200801115533.png 'Virtual ELEMNT BOLT')

## What is this?
virt-elemnt-bolt 
- Concatenates multiple movie files recorded with the action cameras, such as GoPro, and OSMO Action
- Parse [FIT](https://www.thisisant.com/resources/fit-sdk/) data from [Wahoo's ELEMNT BOLT](https://www.wahoofitness.com/devices/bike-computers)
- Generate PNG images to be overlied on the concatenated movie

## Example
[Youtube](https://youtu.be/Zl7oY9ZPXjs)

## Pre-requisites
1. Install fitdecode, matplotlib, tqdm, and opencv-python
```shell
pip3 install fitdecode matplotlib tqdm opencv-python
```

2. Improve the performance to generate PNG images
```shell
pip3 uninstall pillow; export CPATH=`xcrun --show-sdk-path`/usr/include; pip3 install pillow-simd
```

3.Install ffmpeg

virt-elemnt-bolt doesn't use any ffmpeg libs for Python. It calls ffmpeg directly with subprocess as a command line.

For macOS,
```shell
brew install ffmpeg
```

4.Install Roboto font

virt-element-bolt uses [roboto-boldcondensed font](https://fonts2u.com/roboto-bold-condensed.font).

5.Download
```shell
git clone https://github.com/rioriost/virt-elemnt-bolt/
```

6.Add permission
```shell
chmod u+x virt-elemnt-bolt/virt-elemnt-bolt
```

## Usage
```
usage: virt_elemnt_bolt [-h] [--duration DURATION] [--mode {full}]
                        [--output OUTPUT]
                        [--position {left:upper,left:bottom,right:upper,right:bottom}]
                        [--preset {ultrafast,superfast,veryfast,faster,fast,medium,slow,slower,veryslow}]
                        [--save_pngs] [--skip_generate]
                        [--size {0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9,1.0}]
                        fit_path [movie_path [movie_path ...]]

Overlay 'virtual' ELEMNT BOLT on the movie

positional arguments:
  fit_path              Path of a FIT file of ELEMNT BOLT
  movie_path            Path of a movie file(s), /path/to/*.mp4

optional arguments:
  -h, --help            show this help message and exit
  --duration DURATION, -d DURATION
                        Duration to start displaying ELEMNT BOLT (default: 0)
  --mode {full}, -m {full}
                        Display mode of ELEMNT BOLT (default: full)
  --output OUTPUT, -o OUTPUT
                        Path of a directory to save PNG images and
                        concatenated video file (default: virt_elemnt_bolt-
                        output-2020-08-02 15:15:45)
  --position {left:upper,left:bottom,right:upper,right:bottom}, -p {left:upper,left:bottom,right:upper,right:bottom}
                        Position to put ELEMNT BOLT in the movie (default:
                        left:bottom)
  --preset {ultrafast,superfast,veryfast,faster,fast,medium,slow,slower,veryslow}
                        Preset of ffmpeg to overlay PNG images to the movie
                        (default: veryfast)
  --save_pngs           Flag to save PNG images after processing
  --skip_generate       Flag to generate PNG images (to overlay existing PNG
                        images)
  --size {0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9,1.0}, -s {0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9,1.0}
                        Relative height of ELEMNT BOLT to the video (default:
                        0.3)
```
