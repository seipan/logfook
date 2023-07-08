## loghook
<div align="center">
<img src="img/logo.png" alt="属性" title="タイトル">
</div>

 logger to notify logs to slack,discord using webhook 
## Installation
```
go get github.com/seipan/loghook
```

## Usage
When using it, you need to obtain the default webhook for discord and the incoming webhook for slack in advance.
```go
package salck

import "github.com/seipan/loghook"

var (
	// DiscordWebhookURL is a webhook url for discord.
	DiscordWebhookURL = "https://discord.com/api/webhooks/xxxxxxxx/xxxxxxxx"
)

func main() {
	logger := loghook.NewLogger("", "test", "discord", DiscordWebhookURL)
	logger.SetLevel(loghook.DebugLevel)
	logger.SetWebhook(DiscordWebhookURL)

	logger.Debug("test")
	logger.Infof("test %s", "info")

	logger.NoSendDebug()
	logger.Debug("test")
	logger.NoSendInfo()
	logger.Infof("test %s", "info")

    	logger.SetErrorWebhook(DiscordErrorWebhookURL)
	logger.Error("test")
}
```
If you want a more detailed example, please see the [examples](https://github.com/seipan/loghook/blob/main/example).
## License
Code licensed under 
[the MIT License](https://github.com/seipan/loghook/blob/main/LICENSE).
