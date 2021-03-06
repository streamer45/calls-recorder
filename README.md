# calls-recorder

A headless recorder for [Mattermost Calls](https://github.com/mattermost/mattermost-plugin-calls).
This works by running a Docker container that does the following:

- Spawns a Google Chrome browser running on a [`Xvfb`](https://www.x.org/releases/X11R7.6/doc/man/man1/Xvfb.1.xhtml) display.
- Logs in the specified user and connects to the call using [`chromedp`](https://github.com/chromedp/chromedp).
- Grabs the screen and audio using [`ffmpeg`](https://ffmpeg.org) and outputs to a file.
- Creates a post in the specified channel with the recording file attached.

## Usage

### Build docker image

```sh
make docker
```

### Start recording

```sh
MM_SITE_URL="http://localhost:8065" MM_USERNAME="calls-recorder" MM_PASSWORD="" MM_TEAM_NAME="calls" MM_CHANNEL_ID="he1kbdi6kjb3fpte7og9z1zsyo" make run
```

### Stop recording

```sh
make stop
```

## Acknowledgements

Kudos to https://github.com/livekit/livekit-recorder for the idea and code that's been ported here.
