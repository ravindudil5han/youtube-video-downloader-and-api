# YOUTUBE DOWNLOADER

### The code exports a default object with three properties: yt. YT is a function that downloads a YouTube video. It takes five arguments:

* url: a string representing the YouTube video URL
* quality: a string indicating the quality of the video (avaiable options are: 144p, 240p, 360p, 480p, 720p, 1080p, 1440p, 2160p)
* type: a string indicating the type of file (available options are: mp4)
* bitrate: a string indicating the bitrate (available options for video: 144, 240, 360, 480, 720, 1080, 1440, 2160; available option for audio: 128)
* server: a string indicating the server to use (available options: id4, en60, en61, en68)



#### The function returns an object with the following properties:

* dl_link: a string representing the download link of the video
* thumb: a string representing the URL of the video thumbnail
* title: a string representing the title of the video
* filesizeF: a string representing the filesize in its original format (e.g., 12 MB)
* filesize: a number representing the filesize in kilobytes.


![forks](https://img.shields.io/github/forks/ravindudil5han/youtube-video-downloader-and-api?label=Forks&style=social)
![stars](https://img.shields.io/github/stars/ravindudil5han/youtube-video-downloader-and-api?style=social)

![size](https://img.shields.io/github/repo-size/ravindudil5han/youtube-video-downloader-and-api?color=purple&label=Repo%20Size&style=plastic)
![license](https://img.shields.io/github/license/ravindudil5han/youtube-video-downloader-and-api?color=purple&label=License&style=plastic)
![developer](https://img.shields.io/static/v1?label=Author&message=Dilshan&color=purple&style=plastic)


##### For internal use

```
import ytModule from './main.js';

async function downloadVideo(url) {
  try {
    const video = await ytModule.yt(url, '720p', 'mp4', '720'); //Select the bitrate and quality you want
  
    console.log(`Video Title: ${video.title}`);
    console.log(`Video Thumbnail: ${video.thumb}`);
    console.log(`Video File Size: ${video.filesizeF}`);
    console.log(`Video Download Link: ${video.dl_link}`);

    
  } catch (error) {
    console.error(error);
  }
}



const videoURL = 'https://www.youtube.com/watch?v=VJcnuZB4Xt4';
downloadVideo(videoURL);
```

##### For using the Api

```
import { yt } from './main.js'
import express from 'jfteam'



const app = express();
const port = 8080;



app.post('/yt', (req, res) => {
  const { url, quality, type, bitrate, server } = req.body;
  yt(url, quality, type, bitrate, server)
    .then(result => res.json(result))
    .catch(error => res.status(500).json({ error }));
});



app.listen(port, () => console.log(`App listening on port ${port}!`));
```





