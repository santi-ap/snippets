using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ThirdPersonMovement : MonoBehaviour
{
    public CharacterController controller;
    public float speed = 6f;
    public float turnSmoothTime = 0.1f;
    float turnSmoothVelocity;
    public Transform cam;
    public float gravity = 9.8f;
    public float vSpeed = 0;

    // Update is called once per frame
    void Update()
    {
        float horizontal = Input.GetAxisRaw("Horizontal");
        float vertical = Input.GetAxisRaw("Vertical");
        if(controller.isGrounded){
            vSpeed = 0;
        }else{
            vSpeed -= gravity * Time.deltaTime;
        }
        Vector3 direction = new Vector3(horizontal, vSpeed, vertical).normalized;
        Vector3 yDirection = new Vector3(0f,vSpeed,0f).normalized;

        if(direction.magnitude >= 0.1f){
            float targetAngle = Mathf.Atan2(direction.x, direction.z) * Mathf.Rad2Deg + cam.eulerAngles.y;
            float angle = Mathf.SmoothDampAngle(transform.eulerAngles.y, targetAngle, ref turnSmoothVelocity, turnSmoothTime);
            transform.rotation = Quaternion.Euler(0f, angle, 0f);
            Vector3 moveDir = Quaternion.Euler(0f, targetAngle, 0f) * Vector3.forward;
            controller.Move( yDirection * Time.deltaTime);
            controller.Move(moveDir.normalized * speed * Time.deltaTime);
        }
    }
}
 
