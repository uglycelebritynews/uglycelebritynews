

<key>CFBundleURLTypes</key>
<array>
  <dict>
  <key>CFBundleURLSchemes</key>
  <array>
    <string>fbAPP-ID</string>
  </array>
  </dict>
</array>
<key>FacebookAppID</key>
<string>APP-ID</string>
<key>FacebookClientToken</key>
<string>CLIENT-TOKEN</string>
<key>FacebookDisplayName</key>
<string>APP-NAME</string>
// SceneDelegate.swift
import FacebookCore
  ...
func scene(_ scene: UIScene, openURLContexts URLContexts: Set<UIOpenURLContext>) {
    guard let url = URLContexts.first?.url else {
        return
    }

    ApplicationDelegate.shared.application(
        UIApplication.shared,
        open: url,
        sourceApplication: nil,
        annotation: [UIApplication.OpenURLOptionsKey.annotation]
    )
}


// Add this to the header of your file, e.g. in ViewController.swift 
import FacebookLogin

// Add this to the body
class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
	
        let loginButton = FBLoginButton()
        loginButton.center = view.center
        view.addSubview(loginButton)
    }
}

override func viewDidLoad() {
    super.viewDidLoad()

    if let token = AccessToken.current,
        !token.isExpired {
        // User is logged in, do work such as go to next view controller.
    }
}
   
// Extend the code sample from 6a. Add Facebook Login to Your Code
// Add to your viewDidLoad method:
loginButton.permissions = ["public_profile", "email"]
   
